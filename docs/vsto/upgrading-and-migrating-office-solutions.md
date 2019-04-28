---
title: Uaktualnianie i migracja rozwiązań pakietu Office
ms.date: 02/02/2017
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
ms.openlocfilehash: 72f00a5235ac30c65c16da2fd5ef1d900779dbac
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436458"
---
# <a name="upgrade-and-migrate-office-solutions"></a>Uaktualnianie i migracja rozwiązań pakietu Office
  Jeśli masz projekt Microsoft Office, który został utworzony we wcześniejszej wersji programu Visual Studio, musisz uaktualnić projekt, aby używać go w bieżącej wersji programu Visual Studio. Aby uaktualnić projekt Microsoft Office, otwórz go w wersji programu Visual Studio, który zawiera narzędzia Microsoft Office developer tools. Aby uzyskać więcej informacji na temat wersji programu Visual Studio, obejmujących Microsoft Office developer tools, zobacz [Konfigurowanie komputera do opracowywania rozwiązań pakietu Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).

> [!NOTE]
> Zainteresowanych opracowywaniem rozwiązań, które rozszerzają możliwości pakietu Office w [wiele platform](https://dev.office.com/add-in-availability)? Zapoznaj się z nowym [modelu dodatków pakietu Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Dodatki pakietu Office mieć o niewielkich rozmiarach, w porównaniu do dodatków narzędzi VSTO dla programów i rozwiązań, a następnie utworzyć je przy użyciu niemal dowolnej technologii, takich jak HTML5, JavaScript, CSS3 i XML programowanie dla sieci web.

> [!NOTE]
> Program Visual Studio nie może uaktualnić InfoPath z projektów szablonu, które zostały utworzone przy użyciu poprzedniej wersji programu Visual Studio. Te typy projektów nie są obsługiwane w bieżącej wersji programu Visual Studio.

## <a name="changes-to-upgraded-projects"></a>Zmiany do uaktualnionych projektów
 Kiedy uaktualniasz projekt Microsoft Office, Visual Studio modyfikuje projekt, aby docelowe były następujące elementy:

- Visual Studio 2010 Tools dla pakietu Office runtime. Aby uzyskać więcej informacji, zobacz [Visual Studio Tools dla pakietu Office runtime ― omówienie](../vsto/visual-studio-tools-for-office-runtime-overview.md).

- Odwołania bieżącego zestawu.

- Wersja programu .NET Framework, która jest obsługiwana przez typ projektu (po uaktualnieniu do programu Visual Studio 2013 tylko).

- Wersja pakietu Microsoft Office, który jest obsługiwany przez typ projektu (po uaktualnieniu do programu Visual Studio 2013 tylko).

## <a name="assembly-references"></a>Odwołania do zestawów
 Visual Studio uaktualnia następujące odwołania zestawów w projekcie:

- Microsoft Office podstawowe zestawy międzyoperacyjne (PIA).

- Zestawy w [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Aby uzyskać więcej informacji o tych zbiorach, zobacz [Visual Studio Tools dla pakietu Office runtime ― omówienie](../vsto/visual-studio-tools-for-office-runtime-overview.md).

- Nowe lub zaktualizowane wersje zależnych zestawów.

## <a name="targeted-net-framework"></a>Targeted .NET Framework
 Po uaktualnieniu projektu Visual Studio 2013, Visual Studio modyfikuje projekt docelowy: [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] lub [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Wersja programu .NET framework docelowa dla projektu zależy od tego, jakie wersje pakietu Office jest zainstalowany na tym komputerze. Jeśli [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] jest zainstalowany, Visual Studio modyfikuje projekt, który ma być przeznaczony [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. W przeciwnym razie program Visual Studio modyfikuje projekt, który ma być przeznaczony [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].

> [!NOTE]
> Może być konieczne wykonanie dodatkowych kroków, aby uruchomić przekierowane rozwiązanie na komputerach deweloperskich i komputerach użytkowników końcowych, a projekt będzie nie się kompilował jeżeli będzie używał pewnych funkcji. Aby uzyskać więcej informacji, zobacz [Migrowanie rozwiązań pakietu Office do wersji programu .NET Framework 4 lub nowszej](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).

 Jeśli platformą docelową jest [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później w projekcie programu pakietu Office, można użyć niektórych funkcji, które nie są dostępne, gdy platformą docelową jest program .NET Framework 3.5. Aby uzyskać więcej informacji, zobacz [projektowania i tworzenia rozwiązań dla pakietu Office](../vsto/designing-and-creating-office-solutions.md).

## <a name="targeted-office-application"></a>Docelowa aplikacji pakietu Office
 Po uaktualnieniu projektu pakietu Office w Visual Studio 2013, Visual Studio modyfikuje projekt pod kątem określonej wersji pakietu Microsoft Office, który jest obsługiwany przez typ projektu, takich jak projekt dostosowania poziomu dokumentów lub projekt dodatku narzędzi VSTO dla programów.

 Projekty pakietu Office w Visual Studio 2013 można wskazać [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] i [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] aplikacji. Visual Studio modyfikuje projekt przeznaczony dla najnowszej wersji pakietu office, który został zainstalowany. Jeśli żadna z tych wersji pakietu Office są zainstalowane, program Visual Studio nie uaktualnia projektu.

> [!NOTE]
> Jeśli uaktualniasz projekt dodatku narzędzi VSTO do obiektu docelowego [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] lub nowszym, upewnij się, że `ThisAddIn_Startup` program obsługi zdarzeń dodatku narzędzi VSTO dla programów nie zawiera kodu, który uzyskuje dostęp do dokumentu w aplikacji. Aby uzyskać więcej informacji, zobacz [dostęp do dokumentu, podczas uruchamiania aplikacji Office](../vsto/programming-vsto-add-ins.md#AccessingDocuments).

 W przypadku dostosowań poziomu dokumentu [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] Konwertuje dokumenty w projekcie, które mają format binarny, takich jak dokumenty, które mają *xls* lub *doc* rozszerzenia na format Office Open XML. Aby uzyskać więcej informacji dotyczących Open XML, zobacz [wprowadzenie do nowych rozszerzeń nazw plików i Open XML formatuje](https://support.office.com/en-nz/article/Introduction-to-new-file-name-extensions-eca81dcb-5626-4e5b-8362-524d13ae4ec1).

> [!NOTE]
> Tagi inteligentne są przestarzałe w programie Excel 2010 i Word 2010. W związku z tym jeśli rozwiązanie używa inteligentnych tagów, należy usunąć je przed przeprowadzeniem testu i debugowania go w programie Visual Studio 2013 lub Visual Studio 2015.

## <a name="upgrade-microsoft-office-2003-projects"></a>Uaktualnianie projektów Microsoft Office 2003
 Istnieją pewne dodatkowe zagadnienia dotyczące uaktualniania dostosowań na poziomie dokumentu i dodatków narzędzi VSTO dla programów, przeznaczonych dla programu Microsoft Office 2003.

### <a name="document-level-projects"></a>Projektów na poziomie dokumentu
 Jeśli dokument w projekcie zawiera formanty Windows Forms, musi również mieć Visual Studio 2005 Tools for Office Second Edition Runtime zainstalowane przed przystąpieniem do uaktualniania projektu. Jeśli ta wersja środowiska uruchomieniowego nie jest zainstalowany na komputerze deweloperskim przed przystąpieniem do uaktualniania projektu, zaktualizowany projekt może zawierać kompilacji lub błędy wykonania. Po zakończeniu uaktualniania projektu, można odinstalować Visual Studio 2005 Tools for Office Second Edition Runtime z komputera rozwoju Jeśli nie jest on używany przez inne rozwiązania pakietu Office. Ta wersja środowiska uruchomieniowego jest dostępna jako pakiet redystrybucyjny z Microsoft Download Center w [programu Microsoft Visual Studio 2005 Tools for Office Second Edition Runtime (VSTO 2005 SE) (x86)](http://go.microsoft.com/fwlink/?linkid=49612).

### <a name="vsto-add-in-projects"></a>Projekty dodatków narzędzi VSTO
 Jeśli plik rozwiązania oryginalnego projektu Instalatora lub InstallShield Limited Edition projektu, który został skonfigurowany do zainstalowania dodatku narzędzi VSTO, programu Visual Studio uaktualnia projekt, ale nie wprowadza żadnych dalszych zmian do projektu. Jeśli chcesz nadal korzystać z pliku Instalatora Windows do wdrożenia dodatku narzędzi VSTO dla programów, należy zmodyfikować ustawienia lub InstallShield Limited Edition project do zainstalowania nowych wymagań wstępnych, takich jak [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], programu Visual Studio 2010 Tools for Office Runtime i opcjonalnie podstawowe zestawy międzyoperacyjne odwołuje się dodatku narzędzi VSTO dla programów. Aby uzyskać więcej informacji, zobacz [wdrażania rozwiązania pakietu Office przy użyciu Instalatora Windows](../vsto/deploying-an-office-solution-by-using-windows-installer.md).

 Jeśli chcesz używać technologii ClickOnce do wdrażania dodatku narzędzi VSTO dla programów, możesz całkowicie usunąć Instalatora lub InstallShield Limited Edition projekt. Aby uzyskać więcej informacji na temat wdrażania dodatków narzędzi VSTO za pomocą technologii ClickOnce zobacz [wdrożyć rozwiązanie Office](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Aktualizacja rozwiązań pakietu Office](https://msdn.microsoft.com/a269e539-b717-4680-a568-2152b070347e)
- [Migrowanie rozwiązań pakietu Office do wersji programu .NET Framework 4 lub nowszej](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [Okno dialogowe Opcje uaktualniania, projekt](../vsto/project-upgrade-options-dialog-box.md)
