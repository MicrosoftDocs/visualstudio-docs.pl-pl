---
title: Wykonywanie zapytań. Plik PDB | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 13520d6bdf6d6d5e778669bddc08378f4d506bc4
ms.sourcegitcommit: 22b73c601f88c5c236fe81be7ba4f7f562406d75
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/13/2019
ms.locfileid: "56227501"
---
# <a name="querying-the-pdb-file"></a>Używanie zapytań dotyczących pliku .Pdb
Plik bazy danych programu (z rozszerzeniem .pdb) to plik binarny, który zawiera typ i symboliczne informacje debugowania, zbierane w miarę upływu kompilowanie i łączenie projektu. Tworzony jest plik PDB podczas kompilowania programu C/C++ przy użyciu **/zi** lub **/zi** lub [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], lub [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] programowanie z **/debug** Opcja. Pliki obiektów zawierają odwołania do pliku .pdb, aby uzyskać informacje o debugowaniu. Aby uzyskać więcej informacji na temat plików pdb, zobacz [plików PDB](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/yd4f8bd1(v=vs.100)). Aplikacja DIA służy następujące ogólne kroki do uzyskania szczegółowych informacji dotyczących różnych symboli, obiektów i danych elementów w obrębie obrazu wykonywalnego.

### <a name="to-query-the-pdb-file"></a>Do wykonywania zapytań w pliku .pdb

1. Uzyskiwanie źródła danych, tworząc [idiadatasource —](../../debugger/debug-interface-access/idiadatasource.md) interfejsu.

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

2. Wywołaj [idiadatasource::loaddatafrompdb —](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) lub [idiadatasource::loaddataforexe —](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) ładuje te informacje debugowania.

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

3. Wywołaj [idiadatasource::opensession —](../../debugger/debug-interface-access/idiadatasource-opensession.md) otworzyć [idiasession —](../../debugger/debug-interface-access/idiasession.md) do uzyskania dostępu do informacji debugowania.

    ```C++
    CComPtr<IDiaSession> psession;
    if ( FAILED( pSource->openSession( &psession ) ) )
    {
        Fatal( "openSession" );
    }
    ```

4. Używanie metod w `IDiaSession` można wyszukiwać symbole w źródle danych.

    ```C++
    CComPtr<IDiaSymbol> pglobal;
    if ( FAILED( psession->get_globalScope( &pglobal) ) )
    {
        Fatal( "get_globalScope" );
    }
    ```

5. Użyj `IDiaEnum*` informacje o debugowaniu interfejsy do wyliczenia, a następnie przeprowadź skanowanie za pomocą symboli lub inne elementy.

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

## <a name="see-also"></a>Zobacz też
[IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
