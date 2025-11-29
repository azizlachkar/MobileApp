# Quick Reference Guide - Authentication Screens

## 🎨 Color Palette

```xml
<!-- Primary Colors -->
colorPrimary:           #4F46E5  (Indigo 600)
colorPrimaryDark:       #3730A3  (Indigo 800)
colorPrimaryLight:      #818CF8  (Indigo 400)

<!-- Status Colors -->
colorSuccess:           #10B981  (Green)
colorWarning:           #F59E0B  (Amber)
colorError:             #DC2626  (Red)
colorInfo:              #3B82F6  (Blue)

<!-- Neutrals -->
colorOnSurface:         #111827  (Dark)
colorOnSurfaceVariant:  #6B7280  (Gray)
colorBackground:        #F3F4F6  (Light Gray)
white:                  #FFFFFF
```

## 📐 Spacing Scale 

```
XXL:  48dp  (Major sections)
XL:   32dp  (Sections)
L:    24dp  (Cards, margins)
M:    16dp  (Standard spacing)
S:    12dp  (Small spacing)
XS:   8dp   (Minimal spacing)
XXS:  4dp   (Micro spacing)
```

## 🔤 Typography Scale

```
Hero:       36sp  (Welcome screen)
H1:         32sp  (Page headers)
H2:         28sp  (Card titles)
H3:         20sp  (Subheadings)
Body Large: 16sp  (Buttons, inputs)
Body:       15sp  (Info text)
Body Small: 14sp  (Subtitles)
Caption:    12sp  (Helper text)
```

## 🎯 Component Sizes

```
Button Height:          64dp
Input Height:           56dp (with padding)
Avatar Size:            110dp
Icon Container:         100-140dp
Mini FAB:               40dp
Icon Size:              24dp (standard), 32dp (large)
```

## 🔄 Corner Radius

```
Cards:          28dp
Buttons:        16dp
Inputs:         16dp
Small Cards:    12dp
Avatar:         55dp (half of 110dp)
```

## ✨ Elevation

```
Cards:          8-12dp
Buttons:        4dp
Icon Container: 12dp
FAB:            6dp
```

## 🎨 New Icons Created

```xml
ic_email.xml        - Email/envelope icon
ic_lock.xml         - Lock/security icon
ic_phone.xml        - Phone icon
ic_location.xml     - Location pin icon
ic_calendar.xml     - Calendar/date icon
ic_verified.xml     - Checkmark badge icon
ic_celebration.xml  - Party/event icon
```

## 🎬 Animation Files

```xml
fade_in.xml     - 500ms fade in
slide_up.xml    - 400ms slide up + fade
scale_in.xml    - 300ms scale with overshoot
bounce.xml      - 600ms bounce effect
```

## 🎨 Background Drawables

```xml
gradient_primary.xml    - Indigo gradient (135°)
rounded_button.xml      - 16dp rounded shape
circle_background.xml   - Circular shape
```

## 📱 Layout IDs Reference

### Sign In Screen
```
logoContainer       - Logo section
cardAuth           - Main card
emailInputLayout   - Email input wrapper
etEmail            - Email input field
passwordInputLayout - Password input wrapper
etPassword         - Password input field
btnForgotPassword  - Forgot password link
btnLogin           - Sign in button
btnGoSignUp        - Create account button
```

### Sign Up Screen
```
tvHeader           - Page title
tvSubHeader        - Page subtitle
cardForm           - Main form card
imgAvatar          - Avatar image
btnPickPhoto       - Photo picker FAB
etName             - Name input
etEmail            - Email input
etPhone            - Phone input
etAge              - Age input
etAddress          - Address input
etPassword         - Password input
pwStrength         - Password strength indicator
tvPasswordStrength - Strength text
etPassword2        - Confirm password input
swOrganizer        - Organizer switch
btnCreateAccount   - Create account button
btnGoLogin         - Sign in link
```

### Welcome Screen
```
successContainer   - Main content container
imgSuccess         - Success icon
tvWelcome          - Welcome message
btnContinue        - Continue button
btnLogout          - Logout button
```

### Verify Email Screen
```
iconContainer      - Email icon section
imgEmail           - Email icon
cardVerify         - Main card
tvInfo             - Info text
etCode             - Code input field
btnVerify          - Verify button
btnResend          - Resend link
```

## 🎨 Common Patterns

### Material Button (Primary)
```xml
<com.google.android.material.button.MaterialButton
    android:layout_width="match_parent"
    android:layout_height="64dp"
    android:text="Button Text"
    android:textSize="16sp"
    android:textStyle="bold"
    android:textAllCaps="false"
    app:cornerRadius="16dp"
    app:elevation="4dp"
    app:backgroundTint="@color/colorPrimary"
    android:textColor="@color/white"
    app:icon="@drawable/ic_verified"
    app:iconGravity="textEnd"
    app:iconTint="@color/white" />
```

### Material Button (Outlined)
```xml
<com.google.android.material.button.MaterialButton
    style="@style/Widget.Material3.Button.OutlinedButton"
    android:layout_width="match_parent"
    android:layout_height="64dp"
    android:text="Button Text"
    android:textSize="16sp"
    android:textStyle="bold"
    android:textAllCaps="false"
    app:cornerRadius="16dp"
    app:strokeWidth="2dp"
    app:strokeColor="@color/colorPrimary"
    android:textColor="@color/colorPrimary"
    app:icon="@drawable/ic_person"
    app:iconTint="@color/colorPrimary" />
```

### Text Input Layout
```xml
<com.google.android.material.textfield.TextInputLayout
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    style="@style/Widget.Material3.TextInputLayout.OutlinedBox"
    app:boxCornerRadiusTopStart="16dp"
    app:boxCornerRadiusTopEnd="16dp"
    app:boxCornerRadiusBottomStart="16dp"
    app:boxCornerRadiusBottomEnd="16dp"
    app:boxStrokeWidth="2dp"
    app:boxStrokeColor="@color/colorPrimary"
    app:startIconDrawable="@drawable/ic_email"
    app:startIconTint="@color/colorPrimary"
    app:hintTextColor="@color/colorPrimary">

    <com.google.android.material.textfield.TextInputEditText
        android:id="@+id/etEmail"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Email Address"
        android:inputType="textEmailAddress"
        android:textSize="16sp"
        android:padding="16dp" />
</com.google.android.material.textfield.TextInputLayout>
```

### Material Card
```xml
<com.google.android.material.card.MaterialCardView
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    app:cardCornerRadius="28dp"
    app:cardElevation="12dp"
    app:cardBackgroundColor="@color/white">
    
    <!-- Content here -->
    
</com.google.android.material.card.MaterialCardView>
```

### Circular Icon Container
```xml
<FrameLayout
    android:layout_width="120dp"
    android:layout_height="120dp"
    android:background="@drawable/circle_background"
    android:elevation="12dp">
    
    <ImageView
        android:layout_width="70dp"
        android:layout_height="70dp"
        android:layout_gravity="center"
        android:src="@drawable/ic_email"
        android:tint="@color/white" />
</FrameLayout>
```

## 🚀 Quick Implementation Checklist

### For Each Screen:
- [ ] Apply gradient background
- [ ] Add layout animations (`animateLayoutChanges="true"`)
- [ ] Use Material Design 3 components
- [ ] Apply consistent corner radius (16dp, 28dp)
- [ ] Set button heights to 64dp
- [ ] Add custom icons to inputs
- [ ] Use proper spacing (24dp, 16dp, 12dp)
- [ ] Apply elevation to cards (8-12dp)
- [ ] Use typography scale (36sp → 12sp)
- [ ] Add proper content descriptions
- [ ] Test on different screen sizes
- [ ] Verify color contrast ratios

## 📝 Common Tasks

### Change Primary Color
Edit `colors.xml`:
```xml
<color name="colorPrimary">#YOUR_COLOR</color>
```

### Add New Icon
1. Create vector drawable in `res/drawable/`
2. Use 24x24dp viewportWidth/Height
3. Set fillColor to `@color/colorPrimary`

### Apply Animation
```java
View view = findViewById(R.id.viewId);
Animation anim = AnimationUtils.loadAnimation(this, R.anim.fade_in);
view.startAnimation(anim);
```

### Change App Name
Edit `strings.xml`:
```xml
<string name="app_name">Your App Name</string>
```

Update Sign In screen text:
```xml
<TextView
    android:text="Your App Name"
    ... />
```

## 🐛 Common Issues & Fixes

### Issue: Icons not showing
**Fix**: Ensure Material Design library is in dependencies:
```gradle
implementation 'com.google.android.material:material:1.13.0'
```

### Issue: Gradient not appearing
**Fix**: Check drawable is referenced correctly:
```xml
android:background="@drawable/gradient_primary"
```

### Issue: Animations not smooth
**Fix**: Enable hardware acceleration in Activity:
```java
getWindow().setFlags(
    WindowManager.LayoutParams.FLAG_HARDWARE_ACCELERATED,
    WindowManager.LayoutParams.FLAG_HARDWARE_ACCELERATED
);
```

### Issue: Text too small on tablets
**Fix**: Use `sp` units (already done) and test on different screen sizes

### Issue: Colors look different
**Fix**: Ensure you're using the correct color resource:
```xml
android:textColor="@color/colorPrimary"  <!-- Correct -->
android:textColor="#4F46E5"              <!-- Avoid -->
```

## 📚 Resources

- **Material Design 3**: https://m3.material.io/
- **Color Tool**: https://material.io/resources/color/
- **Icon Library**: https://fonts.google.com/icons
- **Animation Guide**: https://developer.android.com/guide/topics/graphics/view-animation

---

**Quick Start**: All layouts are ready to use! Just build and run. Add animations from `ANIMATION_IMPLEMENTATION_GUIDE.md` for enhanced UX.
