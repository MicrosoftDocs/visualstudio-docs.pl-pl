---
title: Ogólne, środowisko, Opcje — okno dialogowe | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.Message.0x800a002e
- VS.ToolsOptionsPages.Environment.General
- VS.Environment.General
helpviewer_keywords:
- MRU lists
- windows, customizing
- MDI, environment options
- speed, environment animation
- File menu
- menus, customizing
- Windows menu customizing
- status bars, displaying
- Visual Studio Start page, setting
- IDE, startup options
- editors, autocompletion
- Options dialog box, General Environment
- General Environment Options dialog box
ms.assetid: 90fc2e6f-572f-4384-96d8-5678299ce58e
caps.latest.revision: 38
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 83fc6adeba0529be03a9a982713d0584a2a7bc45
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661274"
---
# <a name="general-environment-options-dialog-box"></a>Ogólne, środowisko, opcje — Okno dialogowe
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ta strona służy do zmiany motywów kolorów, ustawień paska stanu i skojarzeń rozszerzeń plików między innymi opcjami dla zintegrowanego środowiska programistycznego (IDE). Dostęp do okna dialogowego **Opcje** można uzyskać, otwierając menu **Narzędzia** , wybierając **Opcje**, otwierając folder **środowiska** , a następnie wybierając stronę **Ogólne** . Jeśli ta strona nie jest wyświetlana na liście, zaznacz pole wyboru **Pokaż wszystkie ustawienia** w oknie dialogowym **Opcje** .

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, otwórz menu **Narzędzia** , a następnie wybierz polecenie **Importuj i Eksportuj ustawienia**. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień deweloperskich w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="visual-experience"></a>Środowisko wizualne
 **Motyw kolorów** Wybierz **niebieski**, **jasny** lub **ciemny** motyw koloru dla środowiska IDE.

 Możesz zainstalować dodatkowe wstępnie zdefiniowane motywy i utworzyć niestandardowe motywy, pobierając i instalując **Edytor motywów kolorów programu Visual Studio 2015** z [Visual Studio Marketplace](https://marketplace.visualstudio.com). Po zainstalowaniu tego narzędzia w polu listy motywu kolorów zostaną wyświetlone dodatkowe motywy koloru.

 Zastosuj wielkość liter w menu paska **menu w programie** Visual Studio 2015. Usuń zaznaczenie tej opcji, aby ustawić **wszystkie wersaliki**.

 **Automatycznie Dostosuj środowisko wizualne na podstawie wydajności klienta** Określa, czy program Visual Studio ustawia automatyczne dopasowanie do wizualizacji, czy też ustawia się w sposób jawny. Ta korekta może zmienić sposób wyświetlania kolorów z gradientów na płaskie kolory lub ograniczyć użycie animacji w menu lub oknach podręcznych.

 **Włącz rozbudowane środowisko klienta** Umożliwia pełne środowisko wizualne programu Visual Studio, w tym gradienty i animacje. Wyczyść tę opcję w przypadku używania połączeń Pulpit zdalny lub starszych kart graficznych, ponieważ te funkcje mogą mieć w takich przypadkach niską wydajność. Ta opcja jest dostępna tylko w przypadku usunięcia zaznaczenia opcji **automatycznie Dostosuj środowisko wizualne na podstawie klienta** .

 **Użyj sprzętowego przyspieszania grafiki, jeśli jest dostępne** Używa sprzętowego przyspieszania grafiki, jeśli jest dostępne, a nie przyspieszenia oprogramowania.

## <a name="other"></a>Inne
 **Elementy wyświetlane w menu okno** Dostosowuje liczbę okien, które są wyświetlane na liście systemu Windows w menu **okno** . Wpisz liczbę z zakresu od 1 do 24. Wartość domyślna to 10.

 **Elementy wyświetlane na listach ostatnio używanych** Dostosowuje liczbę ostatnio używanych projektów i plików, które są wyświetlane w menu **plik** . Wpisz liczbę z zakresu od 1 do 24. Wartość domyślna to 10. Jest to prosty sposób na pobranie niedawno używanych projektów i plików.

 **Pokaż pasek stanu** Wyświetla pasek stanu. Pasek stanu znajduje się u dołu okna IDE i wyświetla informacje o postępie trwających operacji.

 **Przycisk zamykania ma wpływ tylko na aktywne okno narzędzi** Określa, że po kliknięciu przycisku **Zamknij** tylko okno narzędzia z fokusem jest zamknięte, a nie wszystkie okna narzędzi w zestawie zadokowanym. Domyślnie ta opcja jest zaznaczona.

 **Przycisk Autoukrywanie ma wpływ tylko na aktywne okno narzędzi** Określa, że po kliknięciu przycisku **Autoukrywanie** tylko okno narzędzia z fokusem jest ukryte automatycznie i nie wszystkie okna narzędzi w zestawie zadokowanym. Domyślnie ta opcja nie jest zaznaczona.

 **Zarządzanie skojarzeniami plików** Wyświetla okno dialogowe **skojarzenia programu Windows Set** , w którym można wyświetlić rozszerzenia plików dla elementów, które są zwykle skojarzone z programem Visual Studio, oraz bieżący program domyślny do otwierania każdego typu pliku. Aby w programie Visual Studio była domyślna aplikacja dla typów plików, które nie są już skojarzone, wybierz rozszerzenie pliku, a następnie wybierz pozycję **Zapisz**.

 Ta opcja może być przydatna, jeśli masz dwie wersje programu Visual Studio zainstalowane na tym samym komputerze i później odinstalujesz jedną z wersji. Po odinstalowaniu ikony plików programu Visual Studio nie będą już wyświetlane w Eksploratorze plików. Ponadto system Windows nie rozpoznaje już programu Visual Studio jako domyślnej aplikacji do edycji tych plików. Ta opcja przywraca te skojarzenia.

## <a name="see-also"></a>Zobacz też
 Okno [dialogowe Opcje środowiska](../../ide/reference/environment-options-dialog-box.md) [dostosowanie układów okna](../../ide/customizing-window-layouts-in-visual-studio.md)
