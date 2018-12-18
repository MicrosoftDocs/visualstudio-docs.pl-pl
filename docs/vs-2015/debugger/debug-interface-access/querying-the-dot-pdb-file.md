---
title: Wykonywanie zapytań. Plik PDB | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- PDB files
- .pdb files, querying
ms.assetid: 8da07d1c-2712-45f9-8fbf-f34040408a8a
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f82180427155a364ad4240eeede0503e99857f80
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51793266"
---
# <a name="querying-the-pdb-file"></a>Używanie zapytań dotyczących pliku .Pdb
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Plik bazy danych programu (z rozszerzeniem .pdb) to plik binarny, który zawiera typ i symboliczne informacje debugowania, zbierane w miarę upływu kompilowanie i łączenie projektu. Tworzony jest plik PDB podczas kompilowania programu C/C++ przy użyciu **/zi** lub **/zi** lub [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], [!INCLUDE[csprcs](../../includes/csprcs-md.md)], lub [!INCLUDE[jsprjscript](../../includes/jsprjscript-md.md)] programowanie z **/debug** Opcja. Pliki obiektów zawierają odwołania do pliku .pdb, aby uzyskać informacje o debugowaniu. Aby uzyskać więcej informacji na temat plików pdb, zobacz [plików PDB](http://msdn.microsoft.com/en-us/1761c84e-8c2c-4632-9649-b5f99964ed3f). Aplikacja DIA służy następujące ogólne kroki do uzyskania szczegółowych informacji dotyczących różnych symboli, obiektów i danych elementów w obrębie obrazu wykonywalnego.  
  
### <a name="to-query-the-pdb-file"></a>Do wykonywania zapytań w pliku .pdb  
  
1.  Uzyskiwanie źródła danych, tworząc [idiadatasource —](../../debugger/debug-interface-access/idiadatasource.md) interfejsu.  
  
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
  
2.  Wywołaj [idiadatasource::loaddatafrompdb —](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) lub [idiadatasource::loaddataforexe —](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) ładuje te informacje debugowania.  
  
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
  
3.  Wywołaj [idiadatasource::opensession —](../../debugger/debug-interface-access/idiadatasource-opensession.md) otworzyć [idiasession —](../../debugger/debug-interface-access/idiasession.md) do uzyskania dostępu do informacji debugowania.  
  
    ```cpp#  
    CComPtr<IDiaSession> psession;  
    if ( FAILED( pSource->openSession( &psession ) ) )   
    {  
        Fatal( "openSession" );  
    }  
    ```  
  
4.  Używanie metod w `IDiaSession` można wyszukiwać symbole w źródle danych.  
  
    ```cpp#  
    CComPtr<IDiaSymbol> pglobal;  
    if ( FAILED( psession->get_globalScope( &pglobal) ) )  
    {  
        Fatal( "get_globalScope" );  
    }  
    ```  
  
5.  Użyj `IDiaEnum*` informacje o debugowaniu interfejsy do wyliczenia, a następnie przeprowadź skanowanie za pomocą symboli lub inne elementy.  
  
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



