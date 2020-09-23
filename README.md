<div align="center">

## Ascii\<\-\-\>Unicode conversion


</div>

### Description

Two small and simple functions for converting from Ascii to Unicode and vice-versa
 
### More Info
 
An Ascii or Unicode string

Target string must be large enough to hold the converted string

On Success: true

On Error: false if any of the strings are NULL

Modifies the target string


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Eugene Ciloci](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/eugene-ciloci.md)
**Level**          |Intermediate
**User Rating**    |4.0 (16 globes from 4 users)
**Compatibility**  |C\+\+ \(general\)
**Category**       |[Strings](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/strings__3-26.md)
**World**          |[C / C\+\+](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/c-c.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/eugene-ciloci-ascii-unicode-conversion__3-3437/archive/master.zip)

### API Declarations

```
/*##############################################################################
CharsetConversion.h
Description: Ascii<->Unicode conversion
Author: Eugene Ciloci (ciloci@sympatico.ca)
Last Modified: Sat Mar 30 02:07:54 2002
##############################################################################*/
#ifndef CHARSET_CONVERSION
#define CHARSET_CONVERSION
#include <stddef.h>
bool AsciiToUnicode(const char * szAscii, wchar_t * szUnicode);
bool UnicodeToAscii(const wchar_t * szUnicode, char * szAscii);
#endif
```


### Source Code

```
/*##############################################################################
CharsetConversion.cpp
Description: Ascii<->Unicode conversion functions
Author: Eugene Ciloci (ciloci@sympatico.ca)
Last Modified: Sat Mar 30 02:07:54 2002
##############################################################################*/
#include <string.h>
#include "CharsetConversion.h"
/*------------------------------------------------------------------------------
Purpose: Convert an Ascii string to Unicode
Parameters: [in] szAscii - Ascii string to be converted
		[out] szUnicode - Unicode string to receive conversion
On Success: szUnicode contains converted string.
		Returns true
On Error: false if either string is NULL
------------------------------------------------------------------------------*/
bool AsciiToUnicode(const char * szAscii, wchar_t * szUnicode)
{
	int len, i;
	if((szUnicode == NULL) || (szAscii == NULL))
		return false;
	len = strlen(szAscii);
	for(i=0;i<len+1;i++)
		*szUnicode++ = static_cast<wchar_t>(*szAscii++);
	return true;
}
/*------------------------------------------------------------------------------
Purpose: Convert a Unicode string to Ascii
Parameters: [in] szUnicode - Unicode string to be converted
			[out] szAscii - Ascii string to receive conversion
On Success: szAscii contains converted string
		Returns true
On Error: false if either string is NULL
------------------------------------------------------------------------------*/
bool UnicodeToAscii(const wchar_t * szUnicode, char * szAscii)
{
	int len, i;
	if((szUnicode == NULL) || (szAscii == NULL))
		return false;
	len = wcslen(szUnicode);
	for(i=0;i<len+1;i++)
		*szAscii++ = static_cast<char>(*szUnicode++);
	return true;
}
```

