---
title: IDebugProgramNode2::GetHostName | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgramNode2::GetHostName
helpviewer_keywords:
- IDebugProgramNode2::GetHostName
ms.assetid: 16aad1ff-ad34-4394-a2e4-5621374a7729
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b7c6642d088da304b0a2d2e48292e8dcbcec1e38
ms.sourcegitcommit: 845442e2b515c3ca1e4e47b46cc1cef4df4f08d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2019
ms.locfileid: "56450038"
---
# <a name="idebugprogramnode2gethostname"></a>IDebugProgramNode2::GetHostName
Pobiera nazwę procesu hostingu programu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetHostName (
    GETHOSTNAME_TYPE dwHostNameType,
    BSTR*            pbstrHostName
);
```

```csharp
int GetHostName (
    enum_GETHOSTNAME_TYPE dwHostNameType,
    out string            pbstrHostName
);
```

#### <a name="parameters"></a>Parametry
`dwHostNameType`  
[in] Wartość z zakresu od [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md) wyliczenie, które określa typ nazwy do zwrócenia.

`pbstrHostName`  
[out] Zwraca nazwę procesu hostingu.

## <a name="return-value"></a>Wartość zwracana
Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="example"></a>Przykład
Poniższy przykład pokazuje, jak zaimplementować tę metodę dla prostego `CProgram` obiekt ujawniający [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) interfejsu. W tym przykładzie ignoruje `dwHostNameType` parametr i zwraca tylko nazwę programu, ponieważ pobierane z podstawowej nazwy ścieżki pliku modułu.

```cpp
HRESULT CProgram::GetHostName(DWORD dwHostNameType, BSTR* pbstrHostName) {
    // Check for valid argument.
    if (pbstrHostName)
    {
        char szModule[_MAX_PATH];

        // Attempt to assign to szModule the path for the file used
        // to create the calling process.
        if (GetModuleFileName(NULL, szModule, sizeof (szModule)))
        {
            // If successful then declare several char arrays
            char  szDrive[_MAX_DRIVE];
            char  szDir[_MAX_DIR];
            char  szName[_MAX_FNAME];
            char  szExt[_MAX_EXT];
            char  szFilename[_MAX_FNAME + _MAX_EXT];
            WCHAR wszFilename[_MAX_FNAME + _MAX_EXT];

            // Break the szModule path name into components.
            _splitpath(szModule, szDrive, szDir, szName, szExt);

            // Copy the base file name szName into szFilename.
            lstrcpy(szFilename, szName);
            // Append the field extension szExt into szFilename.
            lstrcat(szFilename, szExt);

            // Convert the szFilename sequence of multibyte characters
            // to the wszFilename sequence of wide characters.
            mbstowcs(wszFilename, szFilename, sizeof (wszFilename) / 2);

            // Assign the wszFilename to the value at *pbstrHostName.
            *pbstrHostName = SysAllocString(wszFilename);

            return S_OK;
        }
    }

    return E_INVALIDARG;
}
```

## <a name="see-also"></a>Zobacz też
[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)  
[GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md)  
[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
