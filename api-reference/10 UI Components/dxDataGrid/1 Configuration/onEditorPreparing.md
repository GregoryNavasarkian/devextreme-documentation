---
id: dxDataGrid.Options.onEditorPreparing
type: function(e)
default: null
---
---
##### shortDescription
A function used to customize a cell's [editor](/api-reference/_hidden/GridBaseColumn/editorOptions.md '{basewidgetpath}/Configuration/columns/#editorOptions'). Not executed for cells with an [editCellTemplate](/api-reference/_hidden/dxDataGridColumn/editCellTemplate.md '{basewidgetpath}/Configuration/columns/#editCellTemplate').

##### param(e): ui/data_grid:EditorPreparingEvent
Information about the event that caused the function's execution.

##### field(e.cancel): Boolean
Allows you to cancel the editor's creation.        
You can set this field's value to **true** and implement a custom editor.

##### field(e.component): {WidgetName}
The UI component's instance.

##### field(e.dataField): String
The name of the field that supplies data for the column's editor.

##### field(e.disabled): Boolean
Indicates whether the editor is disabled.

##### field(e.editorElement): DxElement
#include common-ref-elementparam with { element: "editor" }

##### field(e.editorName): String
Allows you to change the editor. Accepts names of DevExtreme UI components only, for example, *"dxTextBox"*.      
Import a new editor's module when [DevExtreme modules](/concepts/Common/Modularity/01%20Link%20Modules/10%20Use%20Webpack.md '/Documentation/Guide/Common/Modularity/') are used.

##### field(e.editorOptions): Object
Gets and sets the editor's configuration.

##### field(e.element): DxElement
#include common-ref-elementparam with { element: "UI component" }

##### field(e.parentType): String
The editor's location. One of *"dataRow"*, *"filterRow"*, *"headerRow"* or *"searchPanel"*.      
Properties passed to the function depend on this value.

##### field(e.readOnly): Boolean
Indicates whether the editor is read-only.

##### field(e.row): dxDataGridRowObject
The [properties](/api-reference/10%20UI%20Components/dxDataGrid/6%20Row '/Documentation/ApiReference/UI_Components/dxDataGrid/Row/') of the row's editor.

##### field(e.rtlEnabled): Boolean
Indicates whether the editor uses right-to-left representation.

##### field(e.setValue): any
A method you should call to change the cell value and, optionally, the displayed value after the editor's value is changed.

##### field(e.updateValueTimeout): Number
Gets and sets the delay between when a user stops typing a filter value and the change is applied. Available if the **parentType** is *"filterRow"* or *"searchPanel"*.

##### field(e.value): any
The editor's value. This field is read-only. To change the editor's value, use the **setValue(newValue, newText)** function parameter.

##### field(e.width): Number
The editor's width; equals **null** for all editors except for those whose **parentType** equals *"searchPanel"*.

---
Use this function to:

- Override the default editor's **onValueChanged** handler. For other default editor customizations, use [editorOptions](/api-reference/_hidden/GridBaseColumn/editorOptions.md '{basewidgetpath}/Configuration/columns/#editorOptions').

    ---
    ##### jQuery

        <!-- tab: index.js -->
        $(function() {
            $("#{widgetName}Container").dx{WidgetName}({
                // ...
                onEditorPreparing: function(e) {
                    if (e.dataField === "requiredDataField" && e.parentType === "dataRow") {
                        const defaultValueChangeHandler = e.editorOptions.onValueChanged;
                        e.editorOptions.onValueChanged = function(args) { // Override the default handler
                            // ...
                            // Custom commands go here
                            // ...
                            // If you want to modify the editor value, call the setValue function:
                            // e.setValue(newValue);
                            // Otherwise, call the default handler:
                            defaultValueChangeHandler(args);
                        }
                    }
                }
            });
        });

    ##### Angular

        <!-- tab: app.component.html -->
        <dx-{widget-name} ...
            (onEditorPreparing)="overrideOnValueChanged($event)">
        </dx-{widget-name}>

        <!-- tab: app.component.ts -->
        import { Component } from '@angular/core';

        @Component({
            selector: 'app-root',
            templateUrl: './app.component.html',
            styleUrls: ['./app.component.css']
        })
        export class AppComponent {
            overrideOnValueChanged(e) {
                if (e.dataField === 'requiredDataField' && e.parentType === 'dataRow') {
                    const defaultValueChangeHandler = e.editorOptions.onValueChanged;
                    e.editorOptions.onValueChanged = function (args) { // Override the default handler
                        // ...
                        // Custom commands go here
                        // ...
                        // If you want to modify the editor value, call the setValue function:
                        // e.setValue(newValue);
                        // Otherwise, call the default handler:
                        defaultValueChangeHandler(args);
                    }
                }
            }
        }

        <!-- tab: app.module.ts -->
        import { BrowserModule } from '@angular/platform-browser';
        import { NgModule } from '@angular/core';
        import { AppComponent } from './app.component';

        import { Dx{WidgetName}Module } from 'devextreme-angular';

        @NgModule({
            declarations: [
                AppComponent
            ],
            imports: [
                BrowserModule,
                Dx{WidgetName}Module
            ],
            providers: [],
            bootstrap: [AppComponent]
        })
        export class AppModule { }

    ##### Vue

        <!-- tab: App.vue -->
        <template>
            <Dx{WidgetName} ...
                @editor-preparing="overrideOnValueChanged">
            </Dx{WidgetName}>
        </template>

        <script>
        import 'devextreme/dist/css/dx.light.css';

        import Dx{WidgetName} from 'devextreme-vue/{widget-name}';

        export default {
            components: {
                Dx{WidgetName}
            },
            // ...
            methods: {
                overrideOnValueChanged(e) {
                    if (e.dataField === 'requiredDataField' && e.parentType === 'dataRow') {
                        const defaultValueChangeHandler = e.editorOptions.onValueChanged;
                        e.editorOptions.onValueChanged = function (args) { // Override the default handler
                            // ...
                            // Custom commands go here
                            // ...
                            // If you want to modify the editor value, call the setValue function:
                            // e.setValue(newValue);
                            // Otherwise, call the default handler:
                            defaultValueChangeHandler(args);
                        }
                    }
                }
            }
        }
        </script>

    ##### React

        <!-- tab: App.js -->
        import React from 'react';

        import 'devextreme/dist/css/dx.light.css';

        import {WidgetName} from 'devextreme-react/{widget-name}';

        class App extends React.Component {
            overrideOnValueChanged(e) {
                if (e.dataField === 'requiredDataField' && e.parentType === 'dataRow') {
                    const defaultValueChangeHandler = e.editorOptions.onValueChanged;
                    e.editorOptions.onValueChanged = function (args) { // Override the default handler
                        // ...
                        // Custom commands go here
                        // ...
                        // If you want to modify the editor value, call the setValue function:
                        // e.setValue(newValue);
                        // Otherwise, call the default handler:
                        defaultValueChangeHandler(args);
                    }
                }
            }
            render() {
                return (
                    <{WidgetName} ...
                        onEditorPreparing={this.overrideOnValueChanged}>
                    </{WidgetName}>
                );
            }
        }
        export default App;

    ##### ASP.NET MVC Controls

        <!-- tab: Razor C# -->
        @(Html.DevExtreme().{WidgetName}()
            // ...
            .OnEditorPreparing("overrideOnValueChanged")
        )

        <script type="text/javascript">
            function overrideOnValueChanged(e) {
                if (e.dataField === "requiredDataField" && e.parentType === "dataRow") {
                    const defaultValueChangeHandler = e.editorOptions.onValueChanged;
                    e.editorOptions.onValueChanged = function(args) { // Override the default handler
                        // ...
                        // Custom commands go here
                        // ...
                        // If you want to modify the editor value, call the setValue function:
                        // e.setValue(newValue);
                        // Otherwise, call the default handler:
                        defaultValueChangeHandler(args);
                    }
                }
            }
        </script>

    ---


- Customize editors used in the [search panel](/api-reference/10%20UI%20Components/GridBase/1%20Configuration/searchPanel '{basewidgetpath}/Configuration/searchPanel/'), [filter row](/api-reference/10%20UI%20Components/GridBase/1%20Configuration/filterRow '{basewidgetpath}/Configuration/filterRow/'), and [selection column](/concepts/05%20UI%20Components/DataGrid/15%20Columns/10%20Column%20Types/4%20Command%20Columns/00%20Command%20Columns.md '/Documentation/Guide/UI_Components/{WidgetName}/Columns/Column_Types/Command_Columns/').        
Use the **parentType** function parameter to check if the editor that the function customizes belongs to one of these UI elements.

- [Dynamically change editor properties in the editing state](/concepts/05%20UI%20Components/DataGrid/99%20How%20To/Dynamically%20Change%20Editor%20Properties%20in%20the%20Editing%20State.md '/Documentation/Guide/UI_Components/DataGrid/How_To/Dynamically_Change_Editor_Properties_in_the_Editing_State/').

- Implement other customization cases.

#include btn-open-demo with {
    href: "https://js.devexpress.com/Demos/WidgetsGallery/Demo/DataGrid/CommandColumnCustomization/"
}

[note]

- We do not recommend that you use the **onEditorPreparing** function to specify an editor's default value. Use the [onInitNewRow](/api-reference/10%20UI%20Components/dxDataGrid/1%20Configuration/onInitNewRow.md '{basewidgetpath}/Configuration/#onInitNewRow') function instead.

- This function has the highest priority over the other editing tools. The order of priority is as follows: **onEditorPreparing** > [columns](/api-reference/10%20UI%20Components/dxDataGrid/1%20Configuration/columns '{basewidgetpath}/Configuration/columns/').[formItem](/api-reference/_hidden/GridBaseColumn/formItem.md '{basewidgetpath}/Configuration/columns/#formItem') > [editing](/api-reference/10%20UI%20Components/dxDataGrid/9%20Types/Editing '{basewidgetpath}/Configuration/editing/').[form](/api-reference/10%20UI%20Components/GridBase/1%20Configuration/editing/form.md '{basewidgetpath}/Configuration/editing/#form').

[/note]

#####See Also#####
- **columns[]**.[showEditorAlways](/api-reference/_hidden/GridBaseColumn/showEditorAlways.md '{basewidgetpath}/Configuration/columns/#showEditorAlways')
