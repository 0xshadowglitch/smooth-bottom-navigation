# Smooth Bottom Navigation 🚀

[![Platform](https://img.shields.io/badge/platform-Android-green.svg)](https://developer.android.com)
[![Kotlin](https://img.shields.io/badge/kotlin-1.9.0-purple.svg)](https://kotlinlang.org)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

A lightweight, premium, and fully customizable bottom navigation bar for Android. Designed to provide fluid, high-end animations without the overhead of heavy libraries or Jetpack Compose.

---

## ✨ Features

- **Fluid Transitions**: Smooth morphing from icon to label with a dynamic indicator dot.
- **Micro-Animations**: Translation and scaling effects for a premium native feel.
- **Zero Layout Jank**: Optimized for performance with stable layout structures.
- **Highly Configurable**: Control colors, strokes, corner radius, and icons directly via XML.
- **System-Aware**: Automatically handles system navigation bar insets for edge-to-edge layouts.
- **Dynamic Content**: Supports 2 to 5 navigation items with easy menu-based setup.

---

## 📦 Installation

To integrate **Smooth Bottom Navigation** into your project, simply copy these components:

1.  **View Class**: [CustomBottomNavigationView.kt](app/src/main/java/com/example/custombottomnavigation/CustomBottomNavigationView.kt)
2.  **Layout**: [view_custom_bottom_nav.xml](app/src/main/res/layout/view_custom_bottom_nav.xml)
3.  **Attributes**: [attrs.xml](app/src/main/res/values/attrs.xml)
4.  **Drawables**: `bg_pill.xml` and `circle_blue.xml` (found in `res/drawable`)

---

## 🧩 XML Usage

Add the view to your layout file (e.g., `activity_main.xml`):

```xml
<com.example.custombottomnavigation.CustomBottomNavigationView
    android:id="@+id/custom_nav"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:paddingVertical="4dp"
    android:paddingHorizontal="16dp"
    android:layout_marginBottom="16dp"
    android:elevation="8dp"
    app:menu="@menu/bottom_nav_menu"
    app:defaultSelected="0"
    app:pillStrokeWidth="1dp"
    app:pillStrokeColor="#E0E0E0"
    app:pillBackgroundColor="#FFFFFF"
    app:pillCornerRadius="36dp"
    app:navIconTint="#333333"
    app:layout_constraintBottom_toBottomOf="parent" />
```

### Create a Menu Resource (`res/menu/bottom_nav_menu.xml`)

```xml
<menu xmlns:android="http://schemas.android.com/apk/res/android">
    <item 
        android:id="@+id/nav_home" 
        android:icon="@drawable/ic_home" 
        android:title="Home" />
    <item 
        android:id="@+id/nav_search" 
        android:icon="@drawable/ic_search" 
        android:title="Search" />
    <item 
        android:id="@+id/nav_profile" 
        android:icon="@drawable/ic_profile" 
        android:title="Profile" />
</menu>
```

---

## 🎛️ Customization Attributes

| Attribute | Format | Description | Default |
| :--- | :--- | :--- | :--- |
| `app:menu` | `reference` | The menu resource defining items, icons, and labels. | – |
| `app:defaultSelected` | `integer` | The index (0-indexed) of the item to select on start. | `1` |
| `app:pillStrokeWidth` | `dimension` | Width of the outer container border. | `2dp` |
| `app:pillStrokeColor` | `color` | Color of the outer container border. | `#0B78FF` |
| `app:pillBackgroundColor`| `color` | Background color of the navigation bar. | `#FFFFFF` |
| `app:pillCornerRadius` | `dimension` | Corner radius for the "pill" shape. | `36dp` |
| `app:navIconTint` | `color` | Optional tint applied to all unselected icons. | – |

---

## 🧑‍💻 Programmatic Usage

### Handling Item Selection

```kotlin
val customNav = findViewById<CustomBottomNavigationView>(R.id.custom_nav)

customNav.onItemSelected = { index ->
    when (index) {
        0 -> println("Home Selected")
        1 -> println("Search Selected")
        2 -> println("Profile Selected")
    }
}
```

### Changing State Dynamically

```kotlin
// Change selection via code
customNav.setSelected(2)

// Update icon or label at runtime
customNav.setIcon(0, R.drawable.ic_home_filled)
customNav.setLabel(0, "Dashboard")
```

---

## 📱 Troubleshooting

- **Icons not showing?** Ensure your menu items have `android:icon` attributes pointing to valid drawables.
- **Selection index mismatch?** Remember the indices are **0-based**. If you have 4 items, valid indices are 0, 1, 2, 3.
- **Layout jank?** The view uses `animateLayoutChanges="true"` internally; ensure your parent container isn't forcing heavy layout passes during animations.

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

<p align="center">
  Developed with ❤️ for the Android Community
</p>
