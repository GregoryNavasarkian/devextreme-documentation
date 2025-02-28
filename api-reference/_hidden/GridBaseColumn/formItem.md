---
id: GridBaseColumn.formItem
type: dxFormSimpleItem
---
---
##### shortDescription
Configures the form item that the column produces in the editing state. Applies only if **editing**.[mode](/api-reference/10%20UI%20Components/dxDataGrid/1%20Configuration/editing/mode.md '{basewidgetpath}/Configuration/editing/#mode') is *"form"* or *"popup"*.

---
In the following code, the `Full_Name` grid column in the editing state produces a form item that spans two form columns. The item's label is on top of the editor:

---
##### jQuery

    <!--JavaScript-->
    $(function() {
        $("#{widgetName}Container").dx{WidgetName}({
            // ...
            editing: {
                allowUpdating: true,
                mode: "form"
            },
            columns: [{
                dataField: "Full_Name",
                formItem: {
                    colSpan: 2,
                    label: {
                        location: "top"
                    }
                }
            },
            // ...
            ]
        });
    });

##### Angular
    
    <!--HTML-->
    <dx-{widget-name} ... >
        <dxo-editing
            [allowUpdating]="true"
            mode="form">
        </dxo-editing>
        <dxi-column dataField="Full_Name">
            <dxo-form-item [colSpan]="2">
                <dxo-label location="top"></dxo-label>
            </dxo-form-item>
        </dxi-column>
    </dx-{widget-name}>

    <!--TypeScript-->
    import { Dx{WidgetName}Module } from "devextreme-angular";
    // ...
    export class AppComponent {
        // ...
    }
    @NgModule({
        imports: [
            // ...
            Dx{WidgetName}Module
        ],
        // ...
    })

##### Vue

    <!-- tab: App.vue -->
    <template>
        <Dx{WidgetName} ... >
            <DxEditing
                :allow-updating="true"
                mode="form"
            />
            <DxColumn data-field="Full_Name">
                <DxFormItem :col-span="2">
                    <DxLabel location="top" />
                </DxFormItem>
            </DxColumn>
        </Dx{WidgetName}>
    </template>

    <script>
    import 'devextreme/dist/css/dx.light.css';

    import Dx{WidgetName}, {
        DxEditing,
        DxColumn,
        DxFormItem,
        DxLabel
    } from 'devextreme-vue/{widget-name}';

    export default {
        components: {
            Dx{WidgetName},
            DxEditing,
            DxColumn,
            DxFormItem,
            DxLabel
        },
        // ...
    }
    </script>

##### React

    <!-- tab: App.js -->
    import React from 'react';
    import 'devextreme/dist/css/dx.light.css';

    import {WidgetName}, {
        Editing,
        Column,
        FormItem,
        Label
    } from 'devextreme-react/{widget-name}';

    export default function App() {
        return (
            <{WidgetName} ... >
                <Editing
                    allowUpdating={true}
                    mode="form"
                />
                <Column dataField="Full_Name">
                    <FormItem colSpan={2}>
                        <Label location="top" />
                    </FormItem>
                </Column>
            </{WidgetName}>
        );
    }

##### ASP.NET MVC Controls

    <!--Razor C#-->
    @(Html.DevExtreme().{WidgetName}()
        // ...
        .Editing(e => e
            .AllowUpdating(true)
            .Mode(GridEditMode.Form)
        )
        .Columns(cols => {
            // ...
            cols.Add().DataField("Full_Name")
                .FormItem(item => item
                    .ColSpan(2)
                    .Label(l => l.Location(FormLabelLocation.Top)
                )
            );
        })
    )
    
---

[note]

- The **formItem** object does not allow you to specify a [template](/api-reference/10%20UI%20Components/dxForm/5%20Item%20Types/SimpleItem/template.md '/Documentation/ApiReference/UI_Components/dxForm/Item_Types/SimpleItem/#template'). Use the column's [editCellTemplate](/api-reference/_hidden/dxDataGridColumn/editCellTemplate.md '{basewidgetpath}/Configuration/columns/#editCellTemplate') instead.

- Do not use **formItem** to override editor's **onValueChanged**. Implement [onEditorPreparing](/api-reference/10%20UI%20Components/dxDataGrid/1%20Configuration/onEditorPreparing.md '{basewidgetpath}/Configuration/#onEditorPreparing') instead.

[/note]

#include btn-open-github with {
    href: "https://github.com/DevExpress-Examples/devextreme-datagrid-display-htmleditor-in-form-editing-mode"
}

#####See Also#####
- [Form Edit Mode](/concepts/05%20UI%20Components/DataGrid/20%20Editing/10%20User%20Interaction/40%20Form%20Mode.md '/Documentation/Guide/UI_Components/{WidgetName}/Editing/#User_Interaction/Form_Mode')