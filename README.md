# Reset ASP.NET MVC PivotGrid to Initial State with EnablePersistence

[![License](https://img.shields.io/badge/license-SEE%20LICENSE-blue.svg)](https://www.syncfusion.com/content/downloads/syncfusion_license.pdf)
[![.NET Framework](https://img.shields.io/badge/.NET%20Framework-4.7.2+-512BD4.svg)](https://dotnet.microsoft.com/)
[![Visual Studio](https://img.shields.io/badge/Visual%20Studio-2022-5C2D91.svg)](https://visualstudio.microsoft.com/)
[![Syncfusion EJ2](https://img.shields.io/badge/Syncfusion-EJ2%20MVC-FF6B35.svg)](https://www.syncfusion.com/)

> **Smart PivotGrid State Management** — Implement seamless reset functionality while preserving user preferences with Syncfusion EssentialJS2 PivotGrid persistence in ASP.NET MVC applications.

## 🔍 Overview

This sample application demonstrates a production-ready solution for resetting PivotGrid controls to their initial state without disabling the EnablePersistence feature. Users can customize their PivotGrid configurations—field arrangements, sorting, filtering, and layout—with persistent storage across sessions, while retaining the ability to reset all changes back to default values instantly.

### ✨ Key Features

- ✅ **Smart Reset Functionality** — Clear all customizations while maintaining EnablePersistence
- ✅ **Local Storage State Management** — JavaScript-based persistence using browser localStorage
- ✅ **EssentialJS2 MVC Components** — Enterprise-grade Syncfusion PivotGrid integration
- ✅ **Initial State Capture** — Automatic initial configuration snapshot on first load
- ✅ **User-Friendly Controls** — Simple UI button for one-click state restoration
- ✅ **ASP.NET MVC Best Practices** — Follows MVC patterns with clean architecture
- ✅ **Session Persistence** — Retains user preferences across application sessions

## 🛠 Technology Stack

### Required Technologies
- **Framework**: ASP.NET MVC 5.2.3+
- **Language**: C# 4.5+
- **IDE**: Visual Studio 2022 or Visual Studio Code
- **UI Components**: Syncfusion EJ2 MVC 16.3.0+
- **Frontend**: jQuery 3.5.0, Bootstrap 5.3.3
- **Database**: Entity Framework 6.1.3

### System Requirements
- **.NET Framework**: 4.7.2 or higher
- **Visual Studio**: 2022 Community Edition or Professional
- **Memory**: 2GB minimum
- **Storage**: 500MB for dependencies
- **Browser**: Modern browsers supporting ES6 and localStorage

## 📦 Installation & Setup

### Step 1: Clone or Download the Project
```bash
git clone https://github.com/SyncfusionExamples/mvc-reset-PivotGrid-to-initial-state-while-enabling-EnablePersistence
cd Reset-PivotGrid-to-initial-state-while-enabling-EnablePersistence
```

### Step 2: Open Solution in Visual Studio
1. Launch Visual Studio 2022
2. Click **File → Open → Project/Solution**
3. Navigate to `EssentialJS2MvcApplication2.sln`
4. Click **Open**

### Step 3: Restore NuGet Packages
```bash
# Right-click Solution → Restore NuGet Packages
# Or use Package Manager Console:
Update-Package -Reinstall
```

### Step 4: Build the Solution
```bash
# Press Ctrl+Shift+B or
Build → Build Solution
```

### Step 5: Run the Application
- Press **F5** to start debugging
- Or click the **Run** button in the toolbar
- Application launches at `http://localhost:XXXX`

## 🚀 Quick Start

1. **Build & Run** — Press F5 to launch the application
2. **Navigate to PivotGrid** — Go to the PivotGrid Features page
3. **Customize the Grid** — Drag fields, apply filters, change sorting
4. **Verify Persistence** — Refresh the page; changes persist
5. **Click Reset Button** — Return to initial state instantly
6. **Confirm Active Persistence** — Make new changes; they persist again

## 🧠 How It Works

### Initial State Capture
When the PivotGrid loads for the first time, the application captures and stores the initial configuration:

```javascript
function load() {
    if (window.localStorage.getItem('initialState') === null && 
        window.localStorage.getItem('pivotviewpivot1')) {
        // Store initial state settings in local storage
        window.localStorage.setItem('initialState', 
            window.localStorage.getItem('pivotviewpivotgrid'));
    }
}
```

### Reset Mechanism
When the "Go To Initial State" button is clicked, the stored initial configuration is restored:

```javascript
document.getElementById("state").addEventListener('click', function () {
    var model = JSON.parse(window.localStorage.getItem('initialState'));
    // Reset initial state to grid through setProperties
    document.getElementById('pivotgrid').ej2_instances[0].setProperties(model);
});
```

## 🗂 Project Structure

```
Reset-PivotGrid-to-initial-state-while-enabling-EnablePersistence/
├── Controllers/
│   ├── PivotGridController.cs       # PivotGrid data and logic
│   └── HomeController.cs            # Application entry point
├── Views/
│   ├── PivotGrid/
│   │   └── PivotGridFeatures.cshtml  # Main PivotGrid UI
│   └── Shared/
│       └── _Layout.cshtml           # Master layout
├── Models/                          # Data models and view models
├── Scripts/                         # JavaScript libraries and utilities
├── Content/                         # CSS stylesheets and themes
├── App_Start/                       # Configuration files
├── App_Data/                        # Local database files
└── EssentialJS2MvcApplication2.sln  # Visual Studio solution
```

## ⚙️ Configuration & Customization

### PivotGrid Settings
Modify pivot configuration in `PivotGridFeatures.cshtml`:

```csharp
@Html.EJS().PivotView("pivotgrid")
    .Width("800")
    .Height("300")
    .EnablePersistence(true)           // Enable state persistence
    .ShowFieldList(true)               // Show field list panel
    .ShowGroupingBar(true)             // Show grouping bar
    .DataSource(dataSource => dataSource
        .Data((IEnumerable<object>)ViewBag.Data)
        .Rows(rows => { rows.Name("Country").Add(); })
        .Columns(columns => { columns.Name("Year").Add(); })
        .Values(values => { values.Name("Amount").Add(); }))
    .Render()
```

### Styling and Themes
The application supports multiple themes. Modify the theme reference in `_Layout.cshtml`:
- Fabric theme (default)
- Bootstrap theme
- Material theme
- High Contrast theme

## ❓ Troubleshooting & FAQ

**Q: PivotGrid not persisting changes**
- Ensure `EnablePersistence(true)` is set
- Check browser localStorage is enabled
- Verify no browser privacy settings block localStorage

**Q: Reset button not working**
- Confirm initial state was captured on first load
- Check browser console for JavaScript errors
- Verify localStorage contains 'initialState' key

**Q: Application won't start**
- Ensure .NET Framework 4.7.2+ is installed
- Check all NuGet packages restored successfully
- Verify Visual Studio 2022 installation is complete

**Q: PivotGrid not displaying data**
- Check PivotGridController for data source configuration
- Verify ViewBag.Data contains valid data
- Review browser Network tab for API errors

## 📚 Resources & Documentation

- [ASP.NET MVC Documentation](https://docs.microsoft.com/en-us/aspnet/mvc/)
- [Syncfusion PivotGrid Documentation](https://ej2.syncfusion.com/aspnetmvc/documentation/pivot-table/getting-started)
- [Entity Framework Documentation](https://docs.microsoft.com/en-us/ef/)

## 🤝 Contributing

Contributions are welcome! To contribute:
1. Fork the repository
2. Create a feature branch (`git checkout -b feature/improvement`)
3. Commit changes with clear messages
4. Push to the branch and open a Pull Request

## 📄 License

This project is licensed under the **Syncfusion Community License**. See [Syncfusion License](https://www.syncfusion.com/content/downloads/syncfusion_license.pdf) for details.

## 🆘 Support

For issues, questions, or suggestions:
- Open a GitHub issue with detailed reproduction steps
- Review this README's troubleshooting section
- Check Syncfusion's official documentation
- Submit feature requests via GitHub Discussions
