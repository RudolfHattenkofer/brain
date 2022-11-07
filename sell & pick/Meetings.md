---

database-plugin: basic

---

```yaml:dbfolder
name: sell & pick Meetings
description: 
columns:
  client:
    input: text
    accessorKey: client
    label: client
    key: client
    id: client
    position: 3
    skipPersist: false
    isHidden: false
    sortIndex: -1
    width: 201
    config:
      enable_media_view: true
      link_alias_enabled: true
      media_width: 100
      media_height: 100
      isInline: false
      task_hide_completed: true
  date:
    input: text
    accessorKey: date
    label: date
    key: date
    id: date
    position: 1
    skipPersist: false
    isHidden: false
    sortIndex: -1
    config:
      enable_media_view: true
      link_alias_enabled: true
      media_width: 100
      media_height: 100
      isInline: false
      task_hide_completed: true
  tags:
    input: text
    accessorKey: tags
    label: tags
    key: tags
    id: tags
    position: 4
    skipPersist: false
    isHidden: false
    sortIndex: -1
    config:
      enable_media_view: true
      link_alias_enabled: true
      media_width: 100
      media_height: 100
      isInline: false
      task_hide_completed: true
  __file__:
    key: __file__
    id: __file__
    input: markdown
    label: File
    accessorKey: __file__
    isMetadata: true
    skipPersist: false
    isDragDisabled: false
    csvCandidate: true
    position: 2
    width: 298
    isHidden: false
    sortIndex: -1
    config:
      enable_media_view: true
      link_alias_enabled: true
      media_width: 100
      media_height: 100
      isInline: true
      task_hide_completed: true
config:
  remove_field_when_delete_column: false
  cell_size: normal
  sticky_first_column: false
  group_folder_column: 
  remove_empty_folders: false
  automatically_group_files: false
  hoist_files_with_empty_attributes: true
  show_metadata_created: false
  show_metadata_modified: false
  show_metadata_tasks: false
  show_metadata_inlinks: false
  show_metadata_outlinks: false
  source_data: query
  source_form_result: "FROM \"sell & pick/Meetings\""
  source_destination_path: sell & pick/Meetings
  frontmatter_quote_wrap: false
  row_templates_folder: /
  current_row_template: sell & pick/Meetings/George.md
  pagination_size: 10
  enable_js_formulas: false
  formula_folder_path: /
  inline_default: false
  inline_new_position: top
  date_format: yyyy-MM-dd
  datetime_format: "yyyy-MM-dd HH:mm:ss"
filters:
  enabled: true
  conditions:
```