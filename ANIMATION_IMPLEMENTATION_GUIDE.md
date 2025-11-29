# Animation Implementation Guide

## How to Apply Animations to Your Upgraded Auth Screens

### 1. Sign In Screen Animation

Add this to `SignInActivity.onCreate()`:

```java
@Override
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_sign_in);
    
    // Animate logo container
    View logoContainer = findViewById(R.id.logoContainer);
    Animation scaleIn = AnimationUtils.loadAnimation(this, R.anim.scale_in);
    logoContainer.startAnimation(scaleIn);
    
    // Animate card with delay
    View cardAuth = findViewById(R.id.cardAuth);
    Animation slideUp = AnimationUtils.loadAnimation(this, R.anim.slide_up);
    slideUp.setStartOffset(200); // 200ms delay
    cardAuth.startAnimation(slideUp);
    
    // Existing code...
}
```

### 2. Sign Up Screen Animation

Add this to `SignUpActivity.onCreate()`:

```java
@Override
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_sign_up);
    
    // Animate header
    View tvHeader = findViewById(R.id.tvHeader);
    Animation fadeIn = AnimationUtils.loadAnimation(this, R.anim.fade_in);
    tvHeader.startAnimation(fadeIn);
    
    // Animate card
    View cardForm = findViewById(R.id.cardForm);
    Animation slideUp = AnimationUtils.loadAnimation(this, R.anim.slide_up);
    slideUp.setStartOffset(150);
    cardForm.startAnimation(slideUp);
    
    // Existing code...
}
```

### 3. Welcome Screen Animation

Add this to `WelcomeActivity.onCreate()`:

```java
@Override
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_welcome);
    
    // Animate success icon with bounce
    View imgSuccess = findViewById(R.id.imgSuccess);
    Animation bounce = AnimationUtils.loadAnimation(this, R.anim.bounce);
    imgSuccess.startAnimation(bounce);
    
    // Animate success container
    View successContainer = findViewById(R.id.successContainer);
    Animation fadeIn = AnimationUtils.loadAnimation(this, R.anim.fade_in);
    fadeIn.setStartOffset(300);
    successContainer.startAnimation(fadeIn);
    
    // Existing code...
}
```

### 4. Verify Email Screen Animation

Add this to `VerifyEmailActivity.onCreate()`:

```java
@Override
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_verify_email);
    
    // Animate email icon
    View iconContainer = findViewById(R.id.iconContainer);
    Animation scaleIn = AnimationUtils.loadAnimation(this, R.anim.scale_in);
    iconContainer.startAnimation(scaleIn);
    
    // Animate card
    View cardVerify = findViewById(R.id.cardVerify);
    Animation slideUp = AnimationUtils.loadAnimation(this, R.anim.slide_up);
    slideUp.setStartOffset(200);
    cardVerify.startAnimation(slideUp);
    
    // Existing code...
}
```

## Advanced: Button Click Animations

### Add Ripple Effect and Scale Animation

```java
// For any button
MaterialButton button = findViewById(R.id.btnLogin);
button.setOnClickListener(v -> {
    // Scale animation on click
    v.animate()
        .scaleX(0.95f)
        .scaleY(0.95f)
        .setDuration(100)
        .withEndAction(() -> {
            v.animate()
                .scaleX(1f)
                .scaleY(1f)
                .setDuration(100)
                .start();
        })
        .start();
    
    // Your click logic here
    doLogin();
});
```

## Transition Between Activities

### Add Smooth Transitions

```java
// When navigating from Sign In to Home
Intent intent = new Intent(SignInActivity.this, HomeActivity.class);
startActivity(intent);
overridePendingTransition(android.R.anim.fade_in, android.R.anim.fade_out);
finish();

// When navigating from Sign Up to Sign In
Intent intent = new Intent(SignUpActivity.this, SignInActivity.class);
startActivity(intent);
overridePendingTransition(R.anim.slide_up, android.R.anim.fade_out);
finish();
```

## Input Field Focus Animations

### Animate Input Fields on Focus

```java
TextInputEditText emailInput = findViewById(R.id.etEmail);
emailInput.setOnFocusChangeListener((v, hasFocus) -> {
    if (hasFocus) {
        v.animate()
            .scaleX(1.02f)
            .scaleY(1.02f)
            .setDuration(200)
            .start();
    } else {
        v.animate()
            .scaleX(1f)
            .scaleY(1f)
            .setDuration(200)
            .start();
    }
});
```

## Error Shake Animation

### Create Shake Animation for Errors

Create `res/anim/shake.xml`:

```xml
<?xml version="1.0" encoding="utf-8"?>
<translate xmlns:android="http://schemas.android.com/apk/res/android"
    android:duration="500"
    android:fromXDelta="0"
    android:interpolator="@android:anim/cycle_interpolator"
    android:toXDelta="10" />
```

Use it in code:

```java
// When validation fails
TextInputLayout emailLayout = findViewById(R.id.emailInputLayout);
Animation shake = AnimationUtils.loadAnimation(this, R.anim.shake);
emailLayout.startAnimation(shake);
```

## Loading State Animation

### Show Loading with Progress

```java
MaterialButton btnLogin = findViewById(R.id.btnLogin);

// Show loading
btnLogin.setEnabled(false);
btnLogin.setText("");
btnLogin.setIcon(null);
// Add progress indicator
CircularProgressIndicator progress = new CircularProgressIndicator(this);
progress.setIndeterminate(true);
// Add to button layout

// Hide loading
btnLogin.setEnabled(true);
btnLogin.setText("Sign In");
btnLogin.setIcon(getDrawable(R.drawable.ic_verified));
// Remove progress indicator
```

## Password Strength Animation

### Animate Password Strength Indicator

```java
TextInputEditText passwordInput = findViewById(R.id.etPassword);
LinearProgressIndicator strengthIndicator = findViewById(R.id.pwStrength);
TextView strengthText = findViewById(R.id.tvPasswordStrength);

passwordInput.addTextChangedListener(new TextWatcher() {
    @Override
    public void afterTextChanged(Editable s) {
        int strength = calculatePasswordStrength(s.toString());
        
        // Animate progress
        ObjectAnimator animator = ObjectAnimator.ofInt(
            strengthIndicator, 
            "progress", 
            strengthIndicator.getProgress(), 
            strength
        );
        animator.setDuration(300);
        animator.start();
        
        // Update text and color
        if (strength < 33) {
            strengthText.setText("Weak");
            strengthText.setTextColor(getColor(R.color.colorError));
            strengthIndicator.setIndicatorColor(getColor(R.color.colorError));
        } else if (strength < 66) {
            strengthText.setText("Medium");
            strengthText.setTextColor(getColor(R.color.colorWarning));
            strengthIndicator.setIndicatorColor(getColor(R.color.colorWarning));
        } else {
            strengthText.setText("Strong");
            strengthText.setTextColor(getColor(R.color.colorSuccess));
            strengthIndicator.setIndicatorColor(getColor(R.color.colorSuccess));
        }
    }
    
    // Other methods...
});

private int calculatePasswordStrength(String password) {
    int strength = 0;
    if (password.length() >= 8) strength += 25;
    if (password.matches(".*[A-Z].*")) strength += 25;
    if (password.matches(".*[a-z].*")) strength += 25;
    if (password.matches(".*\\d.*")) strength += 25;
    return strength;
}
```

## Avatar Selection Animation

### Animate Avatar Change

```java
ImageView imgAvatar = findViewById(R.id.imgAvatar);
FloatingActionButton btnPickPhoto = findViewById(R.id.btnPickPhoto);

btnPickPhoto.setOnClickListener(v -> {
    // Open image picker
    // After image selected:
    imgAvatar.animate()
        .alpha(0f)
        .setDuration(150)
        .withEndAction(() -> {
            imgAvatar.setImageURI(selectedImageUri);
            imgAvatar.animate()
                .alpha(1f)
                .setDuration(150)
                .start();
        })
        .start();
});
```

## Success Celebration Animation

### Animate Success State

```java
// After successful verification
View imgSuccess = findViewById(R.id.imgSuccess);
imgSuccess.animate()
    .scaleX(1.2f)
    .scaleY(1.2f)
    .setDuration(200)
    .withEndAction(() -> {
        imgSuccess.animate()
            .scaleX(1f)
            .scaleY(1f)
            .setDuration(200)
            .start();
    })
    .start();
```

## Best Practices

1. **Keep animations short**: 200-500ms for most animations
2. **Use appropriate interpolators**: 
   - `DecelerateInterpolator` for entry animations
   - `AccelerateInterpolator` for exit animations
   - `OvershootInterpolator` for playful effects
3. **Don't overdo it**: Too many animations can be distracting
4. **Test on low-end devices**: Ensure smooth performance
5. **Provide option to disable**: Some users prefer reduced motion
6. **Chain animations properly**: Use `withEndAction()` for sequential animations
7. **Cancel animations on destroy**: Prevent memory leaks

## Performance Tips

```java
// Enable hardware acceleration for better performance
@Override
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    getWindow().setFlags(
        WindowManager.LayoutParams.FLAG_HARDWARE_ACCELERATED,
        WindowManager.LayoutParams.FLAG_HARDWARE_ACCELERATED
    );
    setContentView(R.layout.activity_sign_in);
}

// Cancel animations in onDestroy
@Override
protected void onDestroy() {
    super.onDestroy();
    View view = findViewById(R.id.cardAuth);
    if (view != null) {
        view.clearAnimation();
    }
}
```

---

**Note**: All animations are optional. The layouts look great even without animations, but adding them enhances the user experience significantly.
