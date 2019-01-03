---
title: Identyfikatory GUID i identyfikatory poleceń | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- commands
- id
- command placement
- visual studio command
- guid
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 04d79b78642310b636c6f9e7dd90f86d4f43e1ad
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53902995"
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>Identyfikatory GUID i identyfikatory poleceń programu Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Identyfikator GUID i identyfikator wartości polecenia zawarte w programie Visual Studio zintegrowane środowisko programistyczne (IDE) są definiowane w .vsct — pliki, które są zainstalowane jako część programu Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [IDE-Defined polecenia, menu i grupy](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).

 Aby uzyskać więcej informacji na temat sposobu pracy z obiektami środowiska IDE, które są zdefiniowane w plikach vsct, zobacz [rozszerzanie menu i poleceń](../../extensibility/extending-menus-and-commands.md).

## <a name="finding-a-command-definition"></a>Wyszukiwanie definicji poleceń
 Ponieważ program Visual Studio definiuje więcej niż tysiąc poleceń, to niepraktyczne, wymień je wszystkie w tym miejscu. Zamiast tego wykonaj następujące kroki, aby zlokalizować definicji polecenia.

#### <a name="to-locate-a-command-definition"></a>Aby zlokalizować definicji poleceń

1. W programie Visual Studio, otwórz następujące pliki w *ścieżka instalacji programu Visual Studio SDK*\VisualStudioIntegration\Common\Inc\ folderu: SharedCmdDef.vsct, ShellCmdDef.vsct, VsDbgCmdUsed.vsct, Venusmenu.vsct.

    Większość poleceń programu Visual Studio są definiowane w SharedCmdDef.vsct i ShellCmdDef.vsct. VsDbgCmdUsed.vsct definiuje polecenia, które odnoszą się do debugera i Venusmenu.vsct definiuje polecenia, które są specyficzne dla programowania dla sieci Web.

2. Jeśli polecenie jest element menu, należy pamiętać, dokładny tekst elementu menu. Jeśli polecenie to przycisk na pasku narzędzi, należy pamiętać, tekst etykietki narzędzia, która pojawia się po zatrzymaniu na nim.

3. Naciśnij klawisze CTRL + F, aby otworzyć **znaleźć** okno dialogowe.

4. W **Znajdź** wpisz tekst zanotowaną w kroku 2.

5. Upewnij się, że **wszystkimi otwartymi dokumentami** jest wyświetlany w **przeszukania** pole.

6. Kliknij przycisk **Znajdź następny** przycisk, dopóki nie zostanie zaznaczony tekst w `<Strings>` części [Button Element](../../extensibility/button-element.md).

    `<Button>` Element, który polecenia pojawia się w jest definicji polecenia.

   Po znalezieniu definicji polecenia Kopiuj polecenia można umieścić w innym menu lub paska narzędzi, tworząc [CommandPlacement, Element](../../extensibility/commandplacement-element.md) ma taką samą `guid` i `id` wartości jako polecenie. Aby uzyskać więcej informacji, zobacz [tworzenia wielokrotnego użytku, do grup przycisków](../../extensibility/creating-reusable-groups-of-buttons.md).

### <a name="special-cases"></a>Specjalne przypadki
 W następujących przypadkach tekst menu lub tekst etykietki narzędzia może wyglądać inaczej niż w definicji polecenia.

-   Elementy menu, które obejmują podkreślony znak, takie jak **drukowania** polecenie **pliku** menu, w którym jest podkreślone P.

     Znaki, które są poprzedzone znaku "&" w nazwach elementów menu są wyświetlane jako podkreślony. Jednak .vsct — pliki są zapisywane w pliku XML, który używa znaku "&", aby wskazać znaki specjalne i wymaga, że należy określić handlowe "i", który ma być wyświetlana jako&amp;". W związku z tym, w pliku vsct **drukowania** polecenia jest wyświetlany jako "&amp;drukowania".

-   Polecenia, które mają dynamiczne tekstu, takie jak **Zapisz** *bieżącej, nazwa_pliku*i dynamicznie wygenerowano elementy menu, takie jak elementy **ostatnio używane pliki** listy.

     Nie ma niezawodne możliwości wyszukiwania na dynamiczny tekst. Zamiast tego należy znaleźć grupy, która obsługuje polecenie żądany przez konsultacji [identyfikatory GUID i identyfikatory Visual Studio menu](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) lub [identyfikatory GUID i identyfikatory programu Visual Studio pasków narzędzi](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)i wyszukaj identyfikator tej grupy. Jeśli definicji polecenia nie ma grupy jako jego [elementu nadrzędnego](../../extensibility/parent-element.md), wyszukaj SharedCmdPlace.vsct i ShellCmdPlace.vsct (lub VsDbgCmdPlace.vsct dla poleceń debugera) `<CommandPlacement>` element, który ustawia element nadrzędny polecenie. AndVsDbgCmdPlace.vsct SharedCmdPlace.vsct, ShellCmdPlace.vsct, znajdują się w *ścieżka instalacji programu Visual Studio SDK*\VisualStudioIntegration\Common\Inc\ folderu.

## <a name="see-also"></a>Zobacz też
 [MenuCommands programu Vs. OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md) [tabeli poleceń programu Visual Studio (. Pliki Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) [odwołanie do schematu VSCT XML](../../extensibility/vsct-xml-schema-reference.md)
