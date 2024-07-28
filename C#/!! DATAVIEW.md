```dataview
table file.folder as "Folder", dateformat(file.mtime, "yyyy.MM.dd") as "Modified"
sort file.mtime desc
```