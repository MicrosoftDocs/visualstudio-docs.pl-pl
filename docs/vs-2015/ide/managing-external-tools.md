---
title: Zarządzanie narzędziami zewnętrznymi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.externaltools
helpviewer_keywords:
- Create GUID tool
- RC (Resource Compiler)
- ReBase tool
- Windows NT Message Compiler
- Windows NT C++ Symbol Undecorator
- tstcon32.exe
- Type Library Generator
- Windows NT Image Binder
- tools [Visual Studio], external
- RowsetViewer tool
- utilities, external tools
- Local Test Manager
- OLE DB Rowset Viewer
- Midlc (IDL Compiler)
- ATL Trace Tool
- Odbcte32w.exe
- IDL Compiler
- HCW (Help Workshop)
- Message Compiler [Visual Studio]
- UUID Generator
- MIDL, external tools
- ErrLook tool
- MAKEHM tool
- Error lookup tool
- OLEVIEW (Object Viewer)
- Uuidgen.exe
- WebDbg tool
- OLE/COM Object Viewer
- LTM (Local Test Manager)
- ATLTraceTool.exe
- Bind tool
- Vsvars32.bat
- external tools [Visual Studio]
- ODBC Test
- Windows NT Image Rebaser
- undname.exe
- Vcspawn.exe
- ActiveX Control Test Container
- mc (Message Compiler)
- GUIDGEN tool
- Odbcte32.exe
- DisableMsg tool
- MkTypLib tool
- Help Workshop
- Resource Compiler
ms.assetid: f382fd40-a98f-4934-8c9a-5aeae881acde
caps.latest.revision: 41
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7a9ebda81f013f42aeac23c9c0a8cc5a0a41f5f0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651342"
---
# <a name="managing-external-tools"></a>Zarządzanie narzędziami zewnętrznymi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz wywoływać zewnętrzne narzędzia z wewnątrz programu Visual Studio. Dostępne są kilka domyślnych narzędzi z menu **Narzędzia** , ale można dodać inne własne pliki wykonywalne.

## <a name="tools-available-on-the-visual-studio-tools-menu"></a>Narzędzia dostępne w menu Visual Studio Tools
 Można wywołać następujące narzędzia z menu **Narzędzia** w programie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Możesz również wywołać je według nazwy z okna **szybkiego uruchamiania** . Na przykład, aby wywołać GuidGen.exe, wpisz **Create GUID**.

1. Utwórz identyfikator GUID: generuje identyfikator GUID.

2. Wyszukiwanie błędów: Pobiera komunikat o błędzie z wprowadzonej wartości. Aby uzyskać więcej informacji, zobacz [ERRLOOK Reference](https://msdn.microsoft.com/library/6040ffc1-2355-4a45-8998-84cbcba4ca91).

3. Narzędzie śledzenia ATL/MFC: pokazuje komunikaty śledzenia debugowania w źródłach ATL i MFC.

4. Ochrona przed zaDotfuscatorm: chroni programy .NET przed odwróceniem inżynierów.

5. SPY + +: wyświetla graficznie procesy, wątki, okna i komunikaty okien.

6. Edytor konfiguracji usługi WCF: umożliwia tworzenie i modyfikowanie ustawień konfiguracji usług WCF.

> [!WARNING]
> Może zostać wyświetlona inna lista narzędzi zewnętrznych, w zależności od zainstalowanej wersji programu Visual Studio i profilu ustawień, który został zastosowany. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień deweloperskich w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="adding-new-tools"></a>Dodawanie nowych narzędzi
 Możesz dodać zewnętrzne narzędzie do menu **Narzędzia** . Otwórz okno dialogowe **zewnętrzne narzędzia** , a następnie kliknij przycisk **Dodaj**, a następnie Wypełnij informacje. Na przykład poniższy wpis powoduje otwarcie Eksploratora Windows w katalogu pliku, który jest aktualnie otwarty w programie Visual Studio:

1. Title: Otwórz lokalizację pliku

2. Polecenie: explorer.exe

3. Argumenty:/root, "$ (ItemDir)"

## <a name="arguments-for-external-tools"></a>Argumenty narzędzi zewnętrznych
 Następujące argumenty są zmiennymi programu Visual Studio, które są przypisywane po uruchomieniu zewnętrznego narzędzia. Linki do zewnętrznych narzędzi, takich jak Notepad lub Spy + +, można znaleźć w menu **Narzędzia** przy użyciu okna dialogowego narzędzia zewnętrzne.

> [!NOTE]
> Pasek stanu IDE wyświetla bieżący wiersz i bieżące zmienne kolumn, aby wskazać, gdzie punkt wstawiania znajduje się w aktywnym Edytorze kodu. Bieżąca zmienna tekstowa zwraca tekst lub kod wybrany w tej lokalizacji.

|Nazwa|Argument|Opis|
|----------|--------------|-----------------|
|Ścieżka elementu|$ (Ścieżki elementu)|Pełna nazwa pliku bieżącego pliku (dysk + ścieżka + nazwa pliku).|
|Katalog elementu|$ (ItemDir)|Katalog bieżącego pliku (dysk + ścieżka).|
|Nazwa pliku elementu|$ (ItemFilename)|Nazwa pliku bieżącego pliku (nazwa pliku).|
|Rozszerzenie elementu|$ (ItemExt)|Rozszerzenie nazwy pliku bieżącego pliku.|
|Bieżący wiersz|$ (CurLine)|Pozycja bieżącego wiersza kursora w oknie kodu.|
|Bieżąca kolumna|$ (CurCol)|Bieżąca pozycja kolumny kursora w oknie kodu.|
|Bieżący tekst|$ (CurText)|Zaznaczony tekst.|
|Ścieżka docelowa|$ (TargetPath)|Pełna nazwa pliku elementu do skompilowania (dysk + ścieżka + nazwa pliku).|
|Katalog docelowy|$ (TargetDir)|Katalog elementu do skompilowania.|
|Nazwa obiektu docelowego|$ (TargetName)|Nazwa pliku elementu do skompilowania.|
|Rozszerzenie docelowe|$ (TargetExt)|Rozszerzenie nazwy pliku do skompilowania.|
|Katalog binarny|$ (BinDir)|Końcowa lokalizacja tworzonego pliku binarnego (zdefiniowana jako dysk + ścieżka). Na przykład:** \\ . ..\My Documents\Visual Studio \<Version> \\<ProjectName \> \bin\debug**|
|Katalog projektu|$ (ProjDir)|Katalog bieżącego projektu (dysk + ścieżka).|
|Nazwa pliku projektu|$ (ProjFileName)|Nazwa pliku bieżącego projektu (dysk + ścieżka + nazwa pliku).|
|Katalog rozwiązania|$ (SolutionDir)|Katalog bieżącego rozwiązania (dysk + ścieżka).|
|Nazwa pliku rozwiązania|$ (SolutionFileName)|Nazwa pliku bieżącego rozwiązania (dysk + ścieżka + nazwa pliku).|

## <a name="see-also"></a>Zobacz też
 [Narzędzia kompilacji C/C++](https://msdn.microsoft.com/library/48d9daf4-6bbf-473a-8ce2-bf2923b69f80)
