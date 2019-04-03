---
title: Zarządzanie narzędziami zewnętrznymi | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1a59432d6b630606ac5c133e8a5811186fcf7c34
ms.sourcegitcommit: 40393347a36779230d128f2355a911632a8d458e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58866769"
---
# <a name="managing-external-tools"></a>Zarządzanie narzędziami zewnętrznymi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz wywołać zewnętrznych narzędzi z poziomu programu Visual Studio. Kilka domyślne narzędzia są dostępne z **narzędzia** menu, ale można dodać inne elementy wykonywalne samodzielnie.  
  
## <a name="tools-available-on-the-visual-studio-tools-menu"></a>Narzędzia dostępne w Menu narzędzia programu Visual Studio  
 Możesz wywołać następujących narzędzi z **narzędzia** menu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Można również wywołać za pomocą nazwy z **Szybkie uruchamianie** okna. Na przykład, aby wywołać GuidGen.exe, wpisz **Utwórz GUID**.  
  
1.  Utwórz identyfikator GUID: generuje identyfikator GUID.  
  
2.  Wyszukiwanie błędów: pobiera komunikat o błędzie z wprowadzonej wartości. Aby uzyskać więcej informacji, zobacz [odwołanie ERRLOOK](http://msdn.microsoft.com/library/6040ffc1-2355-4a45-8998-84cbcba4ca91).  
  
3.  Narzędzie śledzenia ATL/MFC: Pokazuje debugowania komunikaty śledzenia w źródłach ATL i MFC.  
  
4.  PreEmptive Protection - Dotfuscator: Chroni programy platformy .NET dla odtwarzania.  
  
5.  SPY++: Wyświetla w postaci graficznej procesy, wątki, windows i komunikatów okien.  
  
6.  Edytor konfiguracji usługi WCF: Umożliwia tworzenie i modyfikowanie ustawień konfiguracji usługi WCF.  
  
> [!WARNING]
>  Może pojawić się różne listy zewnętrznych narzędzi w zależności od wersji programu Visual Studio zainstalowane a profilu ustawień zostały zastosowane. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska deweloperskiego, w programie Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="adding-new-tools"></a>Dodawanie nowych narzędzi  
 Możesz dodać do zewnętrznego narzędzia **narzędzia** menu. Otwórz **zewnętrznych narzędzi** dialogowym i kliknij przycisk **Dodaj**, a następnie wypełnij informacje. Na przykład następujący wpis powoduje Eksploratora Windows, aby otworzyć znajduje się w katalogu pliku, który aktualnie otwarte w programie Visual Studio:  
  
1.  Tytuł: Otwórz lokalizację pliku  
  
2.  Polecenie: explorer.exe  
  
3.  Argumenty: / root, "$(ItemDir)"  
  
## <a name="arguments-for-external-tools"></a>Argumenty dla zewnętrznych narzędzi  
 Następujące argumenty są zmiennymi programu Visual Studio, które przypisano podczas uruchamiania narzędzia zewnętrznego. Łącza do zewnętrznych narzędzi, takich jak Notatnik lub Spy ++, które mogą być wyświetlane na **narzędzia** menu, w oknie dialogowym narzędzia zewnętrzne.  
  
> [!NOTE]
>  Na pasku stanu IDE Wyświetla zmienne bieżący wiersz i bieżącej kolumny, aby wskazać, gdzie znajduje się w edytorze kodu aktywnego punktu wstawiania. Zmienna aktualny tekst zwraca tekst lub kod wybrane w tej lokalizacji.  
  
|Nazwa|Argument|Opis|  
|----------|--------------|-----------------|  
|Ścieżka elementu|$(ItemPath)|Pełnej nazwy pliku bieżącego pliku (dysk i ścieżkę pliku nazwa).|  
|Element katalogu|$(ItemDir)|Katalog bieżącego pliku (dysku i ścieżki).|  
|Nazwa pliku elementu|$(ItemFilename)|Nazwa pliku w bieżącym pliku (nazwa pliku).|  
|Rozszerzenie elementu|$(ItemExt)|Rozszerzenie nazwy pliku bieżącego pliku.|  
|Bieżący wiersz|$(CurLine)|Bieżący wiersz pozycja kursora w oknie kodu.|  
|Bieżąca kolumna|$(CurCol)|Bieżąca kolumna pozycja kursora w oknie kodu.|  
|Aktualny tekst|$(CurText)|Zaznaczony tekst.|  
|Ścieżka docelowa|$(TargetPath)|Pełnej nazwy pliku elementu, który ma zostać utworzony (dysk i ścieżkę pliku nazwa).|  
|Katalog docelowy|$(TargetDir)|Katalog elementu, który ma zostać utworzony.|  
|Nazwa obiektu docelowego|$(TargetName)|Nazwa pliku elementu, który ma zostać utworzony.|  
|Rozszerzenie docelowe|$(TargetExt)|Rozszerzenie nazwy pliku elementu, który ma zostać utworzony.|  
|Katalog danych binarnych|$(BinDir)|Lokalizacji końcowej plik binarny, który jest konstruowany (zdefiniowany jako dysku i ścieżki). Na przykład:**\\... \My Studio \<wersji >\\< nazwa_projektu\>\bin\debug**|  
|Katalog projektu|$(ProjDir)|Katalog bieżący projekt (dysku i ścieżki).|  
|Nazwa pliku projektu|$(ProjFileName)|Nazwa pliku bieżącego projektu (dysk i ścieżkę pliku nazwa).|  
|Katalog rozwiązania|$(SolutionDir)|Katalog bieżącego rozwiązania (dysku i ścieżki).|  
|Nazwa pliku rozwiązania|$(SolutionFileName)|Nazwa pliku bieżącego rozwiązania (dysk i ścieżkę pliku nazwa).|  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzia kompilacji C/C++](http://msdn.microsoft.com/library/48d9daf4-6bbf-473a-8ce2-bf2923b69f80)
