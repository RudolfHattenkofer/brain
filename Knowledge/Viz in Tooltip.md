[Create Views for Tooltips (Viz in Tooltip) - Tableau](https://help.tableau.com/current/pro/desktop/en-us/viz_in_tooltip.htm)

## Basic

```swift
<Sheet name="Sheet" maxwidth="400" maxheight="600" filter="<All fields>">
```

## Filter fields

Simple:

```swift
<Sheet name="Sheet" maxwidth="400" maxheight="600" filter="<business day>">
```

When aggregated:

```swift
<Sheet name="Sheet" maxwidth="400" maxheight="600" filter="<DAY(business day)>">
```



