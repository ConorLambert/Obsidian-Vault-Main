### Compute Server ESG/MPG
- Folder based on RunId
- Calculation Engine first checks if data is contained in one of these folders.
	- Stored in CSV format, one file per time step
- If not, then load from database.

### Results Extraction
- Large files and lengthy process
- User can access the same extracted results that a previous user extracted.