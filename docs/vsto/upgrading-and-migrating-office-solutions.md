---
title: Uaktualnianie i migrowanie rozwiązań pakietu Office
description: Należy uaktualnić projekt, aby używać go w bieżących wersjach programu Visual Studio, jeśli istnieje projekt Offince, który został utworzony we wcześniejszej wersji programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], upgrading
- Office projects [Office development in Visual Studio], upgrading
- upgrading applications [Office development in Visual Studio]
- upgrading Office solutions in Visual Studio
- migrating Office solutions in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b18b61ad6854be654582fe8a8a76da185ec9d89e
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2020
ms.locfileid: "97526611"
---
# <a name="upgrade-and-migrate-office-solutions"></a>Uaktualnianie i migrowanie rozwiązań pakietu Office
  Jeśli masz projekt Microsoft Office, który został utworzony we wcześniejszej wersji programu Visual Studio, musisz uaktualnić projekt, aby używać go w bieżących wersjach programu Visual Studio. Aby uaktualnić projekt Microsoft Office, otwórz go w wersji programu Visual Studio, która zawiera Microsoft Office narzędzia deweloperskie. Aby uzyskać więcej informacji na temat wersji programu Visual Studio, które obejmują narzędzia deweloperskie Microsoft Office, zobacz [Konfigurowanie komputera do opracowywania rozwiązań pakietu Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).

[!include[Add-ins note](includes/addinsnote.md)]

> [!NOTE]
> Program Visual Studio nie może uaktualnić projektów szablonów formularzy programu InfoPath, które zostały utworzone przy użyciu poprzednich wersji programu Visual Studio. Te typy projektów nie są obsługiwane w bieżącej wersji programu Visual Studio.

## <a name="changes-to-upgraded-projects"></a>Zmiany uaktualnionych projektów
 Po uaktualnieniu projektu Microsoft Office Program Visual Studio modyfikuje projekt, aby wskazać następujące elementy:

- Visual Studio 2010 Tools for Office Runtime. Aby uzyskać więcej informacji, zobacz [Visual Studio Tools dla środowiska uruchomieniowego pakietu Office](../vsto/visual-studio-tools-for-office-runtime-overview.md).

- Odwołania bieżącego zestawu.

- Wersja .NET Framework obsługiwana przez typ projektu (w przypadku uaktualnienia do Visual Studio 2013 tylko).

- Wersja Microsoft Office obsługiwana przez typ projektu (w przypadku uaktualnienia do Visual Studio 2013 tylko).

## <a name="assembly-references"></a>Odwołania do zestawów
 Program Visual Studio uaktualnia następujące odwołania do zestawu w projekcie:

- Microsoft Office podstawowe zestawy międzyoperacyjności (zestawów PIA).

- Zestawy w [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Aby uzyskać więcej informacji o tych zestawach, zobacz [Visual Studio Tools dla środowiska uruchomieniowego pakietu Office](../vsto/visual-studio-tools-for-office-runtime-overview.md).

- Nowe lub zaktualizowane wersje zestawów zależnych.

## <a name="targeted-net-framework"></a>.NET Framework do celu
 W przypadku uaktualniania projektu do Visual Studio 2013 program Visual Studio modyfikuje projekt, aby docelowo albo [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . Wersja programu .NET Framework wskazywanego przez projekt zależy od zainstalowanej wersji pakietu Office na komputerze. Jeśli [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] jest zainstalowany, program Visual Studio modyfikuje projekt, aby docelowo [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] . W przeciwnym razie program Visual Studio modyfikuje projekt, aby docelowo [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] .

> [!NOTE]
> Może być konieczne wykonanie pewnych dodatkowych kroków w celu uruchomienia rozwiązania przekierowania na komputerach z systemem deweloperskim i użytkownikami końcowymi, a projekt nie będzie już kompilować, jeśli używa pewnych funkcji. Aby uzyskać więcej informacji, zobacz [Migrowanie rozwiązań pakietu Office do .NET Framework 4 lub nowszego](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).

 Jeśli obiektem docelowym jest [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później w projekcie pakietu Office, można użyć niektórych funkcji, które nie są dostępne w przypadku kierowania .NET Framework 3,5. Aby uzyskać więcej informacji, zobacz [projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md).

## <a name="targeted-office-application"></a>Aplikacja pakietu Office dla aplikacji
 W przypadku uaktualniania projektu pakietu Office do Visual Studio 2013 program Visual Studio modyfikuje projekt, aby docelowa była wersja Microsoft Office, która jest obsługiwana przez typ projektu, na przykład projekt dostosowania na poziomie dokumentu lub projekt dodatku VSTO.

 Projekty pakietu Office w Visual Studio 2013 mogą być ukierunkowane na [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] aplikacje i. Program Visual Studio modyfikuje projekt, tak aby był przeznaczony dla najnowszej zainstalowanej wersji pakietu Office. Jeśli żadna z tych wersji pakietu Office nie jest zainstalowana, program Visual Studio nie uaktualnia projektu.

> [!NOTE]
> Jeśli uaktualniasz projekt dodatku VSTO do elementu docelowego [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] lub nowszego, upewnij się, że `ThisAddIn_Startup` program obsługi zdarzeń dodatku VSTO nie zawiera kodu, który uzyskuje dostęp do dokumentu w aplikacji. Aby uzyskać więcej informacji, zobacz [dostęp do dokumentu podczas uruchamiania aplikacji pakietu Office](../vsto/programming-vsto-add-ins.md#AccessingDocuments).

 W przypadku dostosowań na poziomie dokumentu program [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] konwertuje dokumenty w projekcie, który ma format binarny, taki jak dokumenty z rozszerzeniem *xls* lub *doc* , do formatu Office Open XML. Aby uzyskać więcej informacji na temat programu Open XML, zobacz [wprowadzenie do nowych rozszerzeń nazw plików i otwartych formatów XML](https://support.office.com/en-nz/article/Introduction-to-new-file-name-extensions-eca81dcb-5626-4e5b-8362-524d13ae4ec1).

> [!NOTE]
> Tagi inteligentne są przestarzałe w programie Excel 2010 i Word 2010. W związku z tym, jeśli rozwiązanie używa tagów inteligentnych, należy je usunąć przed przetestować i debugować w programie Visual Studio 2013 lub Visual Studio 2015.

## <a name="upgrade-microsoft-office-2003-projects"></a>Uaktualnianie projektów Microsoft Office 2003
 Istnieją pewne dodatkowe zagadnienia dotyczące uaktualniania dostosowań na poziomie dokumentu i dodatków narzędzi VSTO przeznaczonych dla Microsoft Office 2003.

### <a name="document-level-projects"></a>Projekty na poziomie dokumentu
 Jeśli dokument w projekcie zawiera kontrolki Windows Forms, przed uaktualnieniem projektu należy również zainstalować program Visual Studio 2005 Tools for Office Second Edition Runtime. Jeśli ta wersja środowiska uruchomieniowego nie jest zainstalowana na komputerze deweloperskim przed uaktualnieniem projektu, uaktualniony projekt może zawierać błędy kompilacji lub czasu wykonywania. Po zakończeniu uaktualniania projektu można odinstalować program Visual Studio 2005 Tools for Office Second Edition Runtime z komputera deweloperskiego, jeśli nie jest on używany przez inne rozwiązania pakietu Office. Ta wersja środowiska uruchomieniowego jest dostępna jako pakiet redystrybucyjny z centrum pobierania Microsoft w witrynie [Microsoft Visual Studio 2005 Tools for Office Second Edition Runtime (VSTO 2005 SE) (x86)](https://www.microsoft.com/download/details.aspx?id=2392).

### <a name="vsto-add-in-projects"></a>Projekty dodatków VSTO
 Jeśli plik rozwiązania dla oryginalnego projektu obejmował Instalatora lub projekt InstallShield Limited Edition, który został skonfigurowany do zainstalowania dodatku VSTO, program Visual Studio uaktualnia projekt, ale nie wprowadza żadnych dalszych zmian w projekcie. Jeśli chcesz zachować dodatek Narzędzia VSTO przy użyciu pliku Instalator Windows, musisz zmodyfikować plik Setup lub InstallShield Limited Edition w celu zainstalowania nowych wymagań wstępnych, takich jak [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] , narzędzi Visual Studio 2010 Tools for Office Runtime i opcjonalnie podstawowych zestawów międzyoperacyjnych, do których odwołuje się dodatek VSTO. Aby uzyskać więcej informacji, zobacz [wdrażanie rozwiązania biurowego przy użyciu Instalator Windows](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md).

 Jeśli chcesz użyć technologii ClickOnce do wdrożenia dodatku VSTO, możesz całkowicie usunąć projekt Setup lub InstallShield Limited Edition. Aby uzyskać więcej informacji o wdrażaniu dodatków VSTO przy użyciu technologii ClickOnce, zobacz [wdrażanie rozwiązania pakietu Office](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Zobacz też
- [Instrukcje: Uaktualnianie rozwiązań pakietu Office](/previous-versions/4bez6837(v=vs.140))
- [Migrowanie rozwiązań pakietu Office do .NET Framework 4 lub nowszego](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [Uaktualnianie projektu, Opcje — okno dialogowe](../vsto/project-upgrade-options-dialog-box.md)