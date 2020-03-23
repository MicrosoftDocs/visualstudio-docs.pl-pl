---
title: Uaktualnianie i migrowanie rozwiązań pakietu Office
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
ms.openlocfilehash: 5e421d6e4ee94d9974c0a0583db1fb495c72593e
ms.sourcegitcommit: b32fbbcbc43910b0ed7ce79aa9a22f2ed36ab57e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79416539"
---
# <a name="upgrade-and-migrate-office-solutions"></a>Uaktualnianie i migrowanie rozwiązań pakietu Office
  Jeśli masz projekt pakietu Microsoft Office, który został utworzony we wcześniejszej wersji programu Visual Studio, należy uaktualnić projekt, aby go używać w bieżących wersjach programu Visual Studio. Aby uaktualnić projekt pakietu Microsoft Office, otwórz go w wersji programu Visual Studio zawierającej narzędzia deweloperskie pakietu Microsoft Office. Aby uzyskać więcej informacji na temat wersji programu Visual Studio, które zawierają narzędzia deweloperskie pakietu Microsoft Office, zobacz [Konfigurowanie komputera do tworzenia rozwiązań pakietu Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).

[!include[Add-ins note](includes/addinsnote.md)]

> [!NOTE]
> Program Visual Studio nie może uaktualnić projektów szablonów formularzy programu InfoPath, które zostały utworzone przy użyciu poprzednich wersji programu Visual Studio. Te typy projektów nie są obsługiwane w bieżącej wersji programu Visual Studio.

## <a name="changes-to-upgraded-projects"></a>Zmiany w uaktualnionych projektach
 Podczas uaktualniania projektu pakietu Microsoft Office program Visual Studio modyfikuje projekt w celu kierowania następujących elementów:

- Narzędzia programu Visual Studio 2010 dla środowiska wykonawczego pakietu Office. Aby uzyskać więcej informacji, zobacz [Omówienie środowiska wykonawczego programu Visual Studio Tools for Office](../vsto/visual-studio-tools-for-office-runtime-overview.md).

- Bieżące odwołania do złożenia.

- Wersja programu .NET Framework, która jest obsługiwana przez typ projektu (podczas uaktualniania do programu Visual Studio 2013 tylko).

- Wersja pakietu Microsoft Office obsługiwana przez typ projektu (podczas uaktualniania tylko do programu Visual Studio 2013).

## <a name="assembly-references"></a>Odniesienia do złożenia
 Visual Studio uaktualnia następujące odwołania do zestawu w projekcie:

- Podstawowe zestawy międzyoperacyjne pakietu Microsoft Office (PIA).

- Złożenia w [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]pliku . Aby uzyskać więcej informacji na temat tych zestawów, zobacz [Omówienie środowiska wykonawczego programu Visual Studio Tools for Office](../vsto/visual-studio-tools-for-office-runtime-overview.md).

- Nowe lub zaktualizowane wersje zestawów zależnych.

## <a name="targeted-net-framework"></a>Ukierunkowane ramy .NET
 Po uaktualnieniu projektu do programu Visual Studio 2013 program Visual [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] Studio [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]modyfikuje projekt w celu kierowania na obiekt docelowy lub . Wersja platformy .NET, do której dąży projekt, zależy od wersji pakietu Office zainstalowanej na komputerze. Jeśli [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] jest zainstalowany, Visual Studio modyfikuje projekt do kierowania [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. W przeciwnym razie visual studio modyfikuje projekt do kierowania . [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]

> [!NOTE]
> Może być konieczne wykonanie kilku dodatkowych kroków w celu uruchomienia retargeted rozwiązania na komputerach deweloperskich i użytkowników końcowych, a projekt nie będzie już kompilować, jeśli używa pewnych funkcji. Aby uzyskać więcej informacji, zobacz [Migrowanie rozwiązań pakietu Office do programu .NET Framework 4 lub nowszego](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).

 Jeśli kierujesz [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] reklamy lub później w projekcie pakietu Office, można użyć niektórych funkcji, które nie są dostępne podczas kierowania na program .NET Framework 3.5. Aby uzyskać więcej informacji, zobacz [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md).

## <a name="targeted-office-application"></a>Ukierunkowana aplikacja pakietu Office
 Podczas uaktualniania projektu pakietu Office do programu Visual Studio 2013 program Visual Studio modyfikuje projekt w celu kierowania na wersję pakietu Microsoft Office, która jest obsługiwana przez typ projektu, takich jak projekt dostosowywania na poziomie dokumentu lub projekt dodatku VSTO.

 Projekty pakietu Office w programie Visual [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] Studio [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] 2013 mogą być kierowane na obiekt i aplikacje. Visual Studio modyfikuje projekt do docelowej najnowszej wersji pakietu Office, który został zainstalowany. Jeśli żadna z tych wersji pakietu Office nie jest zainstalowana, program Visual Studio nie uaktualnia projektu.

> [!NOTE]
> Jeśli uaktualnisz projekt dodatku VSTO [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] do celu docelowego `ThisAddIn_Startup` lub nowszego, upewnij się, że program obsługi zdarzeń dodatku VSTO nie zawiera kodu, który uzyskuje dostęp do dokumentu w aplikacji. Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dostępu do dokumentu po uruchomieniu aplikacji pakietu Office](../vsto/programming-vsto-add-ins.md#AccessingDocuments).

 W przypadku dostosowań [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] na poziomie dokumentu konwertuje dokumenty w projekcie, które mają format binarny, na przykład dokumenty z rozszerzeniem *xls* lub *.doc,* na format XML Open pakietu Office. Aby uzyskać więcej informacji na temat otwierania pliku XML, zobacz [Wprowadzenie do nowych rozszerzeń nazw plików i formatów Otwórz XML](https://support.office.com/en-nz/article/Introduction-to-new-file-name-extensions-eca81dcb-5626-4e5b-8362-524d13ae4ec1).

> [!NOTE]
> Tagi inteligentne są przestarzałe w programach Excel 2010 i Word 2010. W związku z tym jeśli rozwiązanie używa tagów inteligentnych, należy je usunąć, zanim będzie można przetestować i debugować go w programie Visual Studio 2013 lub Visual Studio 2015.

## <a name="upgrade-microsoft-office-2003-projects"></a>Uaktualnianie projektów pakietu Microsoft Office 2003
 Istnieją pewne dodatkowe zagadnienia dotyczące uaktualniania dostosowań na poziomie dokumentu i dodatków VSTO przeznaczonych dla pakietu Microsoft Office 2003.

### <a name="document-level-projects"></a>Projekty na poziomie dokumentu
 Jeśli dokument w projekcie zawiera formanty windows forms, przed uaktualnieniem projektu należy również zainstalować środowisko wykonawcze Visual Studio 2005 Tools for Office Second Edition. Jeśli ta wersja środowiska wykonawczego nie jest zainstalowana na komputerze deweloperskim przed uaktualnieniem projektu, uaktualniony projekt może zawierać błędy kompilacji lub wykonywania czasu pracy. Po zakończeniu uaktualniania projektu można odinstalować środowisko uruchomieniowe Visual Studio 2005 Tools for Office Second Edition z komputera dewelopera, jeśli nie jest on używany przez inne rozwiązania pakietu Office. Ta wersja środowiska wykonawczego jest dostępna jako pakiet redystrybucyjny z Centrum pobierania Microsoft w [programie Microsoft Visual Studio 2005 Tools for Office Second Edition Runtime (VSTO 2005 SE) (x86).](https://www.microsoft.com/download/details.aspx?id=2392)

### <a name="vsto-add-in-projects"></a>Projekty dodatków VSTO
 Jeśli plik rozwiązania dla oryginalnego projektu zawiera instalatora lub InstallShield Limited Edition projektu, który został skonfigurowany do zainstalowania dodatku VSTO, Visual Studio uaktualnia projekt, ale nie wprowadzać żadnych dalszych zmian w projekcie. Jeśli chcesz nadal używać pliku Instalatora Windows do wdrażania dodatku VSTO, należy zmodyfikować projekt Instalatora lub InstallShield Limited [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]Edition, aby zainstalować nowe wymagania wstępne, takie jak , Narzędzia programu Visual Studio 2010 dla środowiska wykonawczego pakietu Office i opcjonalnie podstawowe zestawy międzyoperacyjne, do których odwołuje się dodatek VSTO. Aby uzyskać więcej informacji, zobacz [Wdrażanie rozwiązania pakietu Office przy użyciu Instalatora Windows](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md).

 Jeśli chcesz użyć ClickOnce do wdrożenia dodatku VSTO, możesz całkowicie usunąć projekt Instalatora lub InstallShield Limited Edition. Aby uzyskać więcej informacji na temat wdrażania dodatków VSTO przy użyciu funkcji ClickOnce, zobacz [Wdrażanie rozwiązania pakietu Office](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Zobacz też
- [Jak: Uaktualnianie rozwiązań pakietu Office](https://msdn.microsoft.com/a269e539-b717-4680-a568-2152b070347e)
- [Migrowanie rozwiązań pakietu Office do programu .NET Framework 4 lub nowszego](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [Okno dialogowe Uaktualnianie projektu, opcje](../vsto/project-upgrade-options-dialog-box.md)
