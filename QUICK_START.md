# Physio Masr Elite V60 - Quick Start Guide

## Getting Started

### 1. First Time Login
- Open the application
- Enter your name (Marketing Employee Name)
- Click "دخول للتطبيق" (Login to App)

### 2. Main Features

#### Home Page
- View today's planned visits
- See daily visit statistics
- Quick access to daily report PDF
- Add visit notes quickly

#### Add Company
- Company name and zone selection
- Add company contacts (Doctor/Professor/etc.)
- Plan visits for specific days
- Add location via GPS
- Add notes and products/offers
- Bulk add contacts

#### Data Management
- Search companies by name or zone
- Long-press (800ms) on company to edit
- Single tap to view company details
- Edit all company information
- Delete companies (removes all related visits)
- Add/remove products and offers

#### Reports
- **Week Comparison**: See weekly trends with graphs
- **Top Companies**: Most visited companies this month
- **Unvisited**: Companies needing attention
- **Zone Analytics**: Visits by geographical zone

#### Smart Dashboard (Hub)
- **Statistics Tab**: Monthly stats and zone rankings
- **Control Tab**: Plan weekly schedule with drag-and-drop
- Multi-day planning with duplicate prevention

---

## Key Features Explained

### Visit Recording
1. Tap planned company from home page
2. Enter visit notes
3. Click "حفظ الزيارة" (Save Visit)
4. Automatically records time and date

### Company Planning
1. Go to Hub (click username tag)
2. Switch to "Control" tab
3. Select day using tabs
4. Check companies to add
5. Drag to reorder daily schedule

### PDF Reports
- Daily report: Home page → "📄 ملف PDF اليوم"
- Monthly report: Reports page → "📄 تحميل تقرير الشهر"
- Auto-includes company details and zones

### Data Backup
- **Export**: Click export in dropdown
- **Import**: Upload previously exported JSON file
- Backup before major changes

---

## Troubleshooting

### Data Not Saving?
- Check browser allows localStorage
- Try refreshing page
- Export/Import as backup

### PDF Not Generating?
- Ensure no visits recorded yet for selected period
- Try again after recording visits
- Check browser console for errors

### Touch Events Not Working?
- Long-press = 800ms hold to edit
- Single tap = quick view
- Swipe not used (can scroll)

### Search Not Working?
- Check spelling of company/zone name
- Clear search field and try again
- Try searching by zone

---

## Mobile Tips

1. **Long-Press**: Hold finger on company for 800ms to edit
2. **Scroll**: Swipe up/down to see more companies
3. **Back**: Use browser back button or close button
4. **Data**: Works offline, syncs on next load

---

## Data Structure

### Company Object
```
{
  name: string,
  zone: string,
  persons: [ { title, name, phone } ],
  location: URL,
  plannedDays: [0-4],
  notes: string,
  products: [string],
  createdAt: ISO date
}
```

### Visit Object
```
{
  company: string,
  note: string,
  date: dateString,
  timestamp: timeString,
  id: number
}
```

---

## Keyboard Shortcuts

| Action | Shortcut |
|--------|----------|
| Add product | Enter key in product input |
| Save changes | Click button (No keyboard shortcut) |
| Navigate | Tab key between fields |

---

## Performance Tips

1. Keep company list < 200 entries for best performance
2. Archive old visits regularly
3. Use zones to organize companies
4. Export data monthly as backup

---

## Browser Requirements

- Modern browser (2020+)
- 5MB localStorage available
- JavaScript enabled
- Geolocation for GPS (optional)

---

## Contact & Support

For issues or feature requests:
1. Check DEVELOPMENT_SUMMARY.md for technical details
2. Verify all data is saved (refresh page)
3. Export data to backup
4. Clear browser cache if issues persist

---

## Version Information

- **Name**: Physio Masr Elite V60
- **Version**: 1.1.0
- **Status**: Production Ready
- **Last Updated**: 2026-05-10

---

## Common Workflows

### Daily Workflow
1. View planned companies (Home)
2. Record each visit as completed
3. View daily report
4. Export PDF if needed

### Weekly Planning
1. Open Dashboard Hub
2. Switch to Control tab
3. Plan companies for each day
4. Save and refresh

### Monthly Reporting
1. Go to Reports page
2. Check top companies
3. Monitor unvisited companies
4. Generate PDF report

### Data Management
1. Regularly export backups
2. Edit company details as needed
3. Track contact information
4. Monitor zone coverage

---

## Feature Checklist

- [x] Add/Edit/Delete companies
- [x] Record visits with notes
- [x] Plan weekly schedule
- [x] View reports and analytics
- [x] Export/Import data
- [x] PDF reports
- [x] Mobile-friendly interface
- [x] Long-press editing
- [x] GPS location tracking
- [x] Product tracking
- [x] Multi-day planning
- [x] Drag-and-drop scheduling
- [x] Zone-based analytics

---

**Happy Working with Physio Masr Elite V60! 📊**
