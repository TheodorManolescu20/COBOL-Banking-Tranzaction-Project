# COBOL-Banking-Tranzaction-Project

  This COBOL initiative is formulated with the purpose of handling input records derived from an input file and producing output records in accordance with defined business rules. The program systematically retrieves data from the INP-FILE, conducts processing operations, incorporating updates from the COM-FILE, and subsequently records the outcomes in both the OUT-FILE and REP-FILE.  A thorough presentation of the project's structure and operational logic ensues..

  Project Structure:
  
    Identification Division:
    
         Program ID: COBFILE2
         
    Environment Division:
    
      Configuration Section: Configures special names and file connections.
      Input-Output Section: Defines file structures and their statuses.
      
    Data Division:
    
      File Section: This segment delineates the formats of the input (INP-FILE), output (OUT-FILE, REP-FILE), and rejection (REJ-FILE) files.
      Working-Storage Section: Encompassing this section are variables and flags essential for validation and processing purposes.
      Copy Sections: Within this category are incorporated copybooks (e.g., CPYCOM, CPYINP1, CPYOUT1, CPYREJ1) housing schema definitions and additional data structures.
      
    Procedure Division:
    
      Open Files: Opens input, output, and commission files.
      Write Headers: Writes headers to REP-FILE.
      Read Input File: Reads records from INP-FILE.
      Process Records: Validates input, processes records, updates commission data, and generates output records.
      Write Reject Records: Writes rejected records to REJ-FILE.
      Write Output Records: Writes processed records to OUT-FILE.
      Process Report: Processes data for the report.
      Build Report: Builds the report records.
      Write Report: Writes report records to REP-FILE.
      Write Footers: Writes footer records to REP-FILE.
      Close Files: Closes all files.
      
    Program Logic:
    
      Initialization and File Handling:
      The program initiates the opening of input (INP-FILE), output (OUT-FILE, REP-FILE), rejection (REJ-FILE), and commission (COM-FILE) files.
      Record Processing:
        - Retrieves records from the INP-FILE.
        - Validates input records against various criteria such as date format, currency, and schema conformity.
        - Redirects invalid records to the REJ-FILE.
        - Processes valid records, modifying commission data in the COM-FILE, and generating output records in the OUT-FILE.
        - Calculate total amounts and transaction counts based on schema and card type.
        
    Report Generation:
    
        - Constructs and records header entries in the REP-FILE.
        - Analyzes input records to generate a report, accumulating totals for valid transactions.
        - Inscribes report records in the REP-FILE.
        - Documents footer entries, encompassing rejection counts, system date, and time, in the REP-FILE.
        
    Error Handling:
    
        - Manages file-related errors (opening, reading, writing, and closing) by displaying error messages and invoking a subroutine (ILBOABN0).
    Commission File Update:
        - Reads and modifies commission data from the COM-FILE based on input records.
        
    Notes:
    
        The program effectively directs the validation and processing flow using a range of flags, such as SW-VALID and SW-INVAL.
        To facilitate reporting, it meticulously tracks count and total variables like CN-AMNT-TOT and CN-NO-OF-REC.
        Date validation and processing operations leverage the WS-DATE-FOR-LINKAGE and COBTEST1 subroutine. 
        Commission data is extracted from and written to the COM-FILE, with updates tailored to input records. 
        The program accumulates and logs report records in the REP-FILE. It adeptly handles both valid and invalid input records, ensuring precise error logging and rejection count tracking.
  
