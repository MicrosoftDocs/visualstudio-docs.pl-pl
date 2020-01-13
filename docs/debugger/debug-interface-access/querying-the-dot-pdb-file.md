---
title: Wykonywanie zapytania dotyczącego. Plik PDB | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- PDB files
- .pdb files, querying
ms.assetid: 8da07d1c-2712-45f9-8fbf-f34040408a8a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a22bc8fbe65795a3c5162607a12690081e565666
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2020
ms.locfileid: "75917103"
---
# <a name="querying-the-pdb-file"></a>Używanie zapytań dotyczących pliku .Pdb
Plik bazy danych programu (rozszerzenie. pdb) to plik binarny, który zawiera informacje o typie i symbolicznym debugowaniu zebrane w trakcie kompilowania i łączenia projektu. Plik PDB jest tworzony podczas kompilowania w języku C/C++ programu z **/Zi** lub **/ZI** lub programem [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]lub [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] z opcją **/Debug** . Pliki obiektów zawierają odwołania do pliku. pdb na potrzeby debugowania informacji. Aby uzyskać więcej informacji na temat plików PDB, zobacz [pliki PDB](/previous-versions/visualstudio/visual-studio-2010/yd4f8bd1(v=vs.100)). Aplikacja DIA może użyć następujących ogólnych kroków, aby uzyskać szczegółowe informacje dotyczące różnych symboli, obiektów i elementów danych w obrazie wykonywalnym.

### <a name="to-query-the-pdb-file"></a>Aby wysłać zapytanie do pliku. pdb

1. Pobierz źródło danych, tworząc Interfejs [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) .

    ```C++
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

    ```C++
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

    ```C++
    CComPtr<IDiaSession> psession;
    if ( FAILED( pSource->openSession( &psession ) ) )
    {
        Fatal( "openSession" );
    }
    ```

4. Użyj metod w `IDiaSession`, aby wykonać zapytanie dotyczące symboli w źródle danych.

    ```C++
    CComPtr<IDiaSymbol> pglobal;
    if ( FAILED( psession->get_globalScope( &pglobal) ) )
    {
        Fatal( "get_globalScope" );
    }
    ```

5. Użyj interfejsów `IDiaEnum*`, aby wyliczyć i przeskanować symbole lub inne elementy informacji debugowania.

    ```C++
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

## <a name="see-also"></a>Zobacz także
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
