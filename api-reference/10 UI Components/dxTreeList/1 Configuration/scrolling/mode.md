---
id: dxTreeList.Options.scrolling.mode
---
---
##### shortDescription
Specifies the scrolling mode.

---
The following scrolling modes are available in the UI component:

- **Standard**      
Rows are rendered at once or by pages if [paging](/api-reference/10%20UI%20Components/dxTreeList/1%20Configuration/paging '/Documentation/ApiReference/UI_Components/dxTreeList/Configuration/paging/') is enabled. Scrolling appears only if all the rows cannot fit into the UI component's height.

- **Virtual**       
This mode is an alternative to paging where pages are rendered when they get into the viewport and removed once they leave it. Use this mode if a user should be able to scroll data by pages. Node selection in **virtual** scroll mode with Shift+Click does not work in the following cases: 
    - Deferred selection is enabled.
    - Rows grouping is enabled.
    - The [allowSelectAll](/api-reference/10%20UI%20Components/GridBase/1%20Configuration/selection/allowSelectAll.md 'Documentation/ApiReference/UI_Components/dxDataGrid/Configuration/selection/#allowSelectAll') property is disabled.

[note] Specify the component's [height](/api-reference/10%20UI%20Components/DOMComponent/1%20Configuration/height.md '/Documentation/ApiReference/UI_Components/dxTreeList/Configuration/#height') if you use virtual scrolling.

Note that the [rowRenderingMode](/api-reference/10%20UI%20Components/dxTreeList/1%20Configuration/scrolling/rowRenderingMode.md '{basewidgetpath}/Configuration/scrolling/#rowRenderingMode') property value is "*virtual*" and cannot be changed if you set the **mode** property to "*virtual*" or "*standard*".

Regardless of the scrolling mode, you can use the **paging**.[pageSize](/api-reference/10%20UI%20Components/GridBase/1%20Configuration/paging/pageSize.md '/Documentation/ApiReference/UI_Components/dxTreeList/Configuration/paging/#pageSize') property to specify the number of rows on a page.
