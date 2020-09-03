---
title: Wykonywanie zapytania dotyczącego. Plik PDB | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- PDB files
- .pdb files, querying
ms.assetid: 8da07d1c-2712-45f9-8fbf-f34040408a8a
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9b9013d41ac4d5ca890e7cc9e09b5eb9415cb640
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691327"
---
# <a name="querying-the-pdb-file"></a>Używanie zapytań dotyczących pliku .Pdb
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Plik bazy danych programu (rozszerzenie. pdb) to plik binarny, który zawiera informacje o typie i symbolicznym debugowaniu zebrane w trakcie kompilowania i łączenia projektu. Plik PDB jest tworzony podczas kompilowania programu C/C++ z **/Zi** lub **/Zi** lub [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] , [!INCLUDE[csprcs](../../includes/csprcs-md.md)] lub [!INCLUDE[jsprjscript](../../includes/jsprjscript-md.md)] program z opcją **/Debug** . Pliki obiektów zawierają odwołania do pliku. pdb na potrzeby debugowania informacji. Aby uzyskać więcej informacji na temat plików PDB, zobacz [pliki PDB](https://msdn.microsoft.com/1761c84e-8c2c-4632-9649-b5f99964ed3f). Aplikacja DIA może użyć następujących ogólnych kroków, aby uzyskać szczegółowe informacje dotyczące różnych symboli, obiektów i elementów danych w obrazie wykonywalnym.  
  
### <a name="to-query-the-pdb-file"></a>Aby wysłać zapytanie do pliku. pdb  
  
1. Pobierz źródło danych, tworząc Interfejs [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) .  
  
    ```cpp#  
    CComPtr<IDiaDataSource> pSource;  
    hr = CoCreateInstance( CLSID_DiaSource,  
                           NULL,  
                           CLSCTX_INPROC_SERVER,  
                           __uuidof( IDiaDataSource ),  
                          (void **) &pSource);  
  
    if (FAILED(hr))  
    {  
        Fatal("Could not CoCreate CLSID_DiaSource. Register msdia80.dll." );  
    }  
    ```  
  
2. Wywołanie [IDiaDataSource:: loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) lub [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) w celu załadowania informacji o debugowaniu.  
  
    ```cpp#  
    wchar_t wszFilename[ _MAX_PATH ];  
    mbstowcs( wszFilename, szFilename, sizeof( wszFilename )/sizeof( wszFilename[0] ) );  
    if ( FAILED( pSource->loadDataFromPdb( wszFilename ) ) )  
    {  
        if ( FAILED( pSource->loadDataForExe( wszFilename, NULL, NULL ) ) )  
        {  
            Fatal( "loadDataFromPdb/Exe" );  
        }  
    }  
    ```  
  
3. Wywołaj [IDiaDataSource:: openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) , aby otworzyć [IDiaSession](../../debugger/debug-interface-access/idiasession.md) w celu uzyskania dostępu do informacji o debugowaniu.  
  
    ```cpp#  
    CComPtr<IDiaSession> psession;  
    if ( FAILED( pSource->openSession( &psession ) ) )   
    {  
        Fatal( "openSession" );  
    }  
    ```  
  
4. Użyj metod w programie, `IDiaSession` Aby wykonać zapytanie dotyczące symboli w źródle danych.  
  
    ```cpp#  
    CComPtr<IDiaSymbol> pglobal;  
    if ( FAILED( psession->get_globalScope( &pglobal) ) )  
    {  
        Fatal( "get_globalScope" );  
    }  
    ```  
  
5. Użyj `IDiaEnum*` interfejsów, aby wyliczyć i przeskanować symbole lub inne elementy informacji debugowania.  
  
    ```cpp#  
    CComPtr<IDiaEnumTables> pTables;  
    if ( FAILED( psession->getEnumTables( &pTables ) ) )  
    {  
        Fatal( "getEnumTables" );  
    }  
    CComPtr< IDiaTable > pTable;  
    while ( SUCCEEDED( hr = pTables->Next( 1, &pTable, &celt ) ) && celt == 1 )  
    {  
         // Do something with each IDiaTable.  
    }  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
