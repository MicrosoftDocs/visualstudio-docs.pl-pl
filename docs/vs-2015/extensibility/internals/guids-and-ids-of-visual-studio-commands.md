---
title: Identyfikatory GUID i ID poleceń | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands
- id
- command placement
- visual studio command
- guid
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2feef3cbe72b7eb8db96052236fe483733e22273
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538141"
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>Identyfikatory GUID i identyfikatory poleceń programu Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wartości identyfikatora GUID i identyfikatora poleceń zawartych w zintegrowanym środowisku programistycznym (IDE) programu Visual Studio są zdefiniowane w plikach. vsct, które są instalowane w ramach zestawu Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [polecenia, menu i grupy zdefiniowane przez środowisko IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).

 Aby uzyskać więcej informacji na temat sposobu pracy z obiektami IDE zdefiniowanymi w plikach. vsct, zobacz [rozszerzanie menu i poleceń](../../extensibility/extending-menus-and-commands.md).

## <a name="finding-a-command-definition"></a>Znajdowanie definicji polecenia
 Ponieważ program Visual Studio definiuje więcej niż 1000 poleceń, nie jest praktyczne, aby wyświetlić je w tym miejscu. Zamiast tego wykonaj następujące kroki, aby zlokalizować definicję polecenia.

#### <a name="to-locate-a-command-definition"></a>Aby zlokalizować definicję polecenia

1. W programie Visual Studio Otwórz następujące pliki w *ścieżce instalacji zestawu SDK programu Visual Studio*\VisualStudioIntegration\Common\Inc\ folder: SharedCmdDef. vsct, ShellCmdDef. vsct, VsDbgCmdUsed. vsct, Venusmenu. vsct.

    Większość poleceń programu Visual Studio jest zdefiniowanych w SharedCmdDef. vsct i ShellCmdDef. vsct. VsDbgCmdUsed. vsct definiuje polecenia, które odnoszą się do debugera, a Venusmenu. vsct definiuje polecenia, które są specyficzne dla programowania w sieci Web.

2. Jeśli polecenie jest elementem menu, należy zwrócić uwagę na dokładny tekst elementu menu. Jeśli polecenie jest przyciskiem na pasku narzędzi, należy zwrócić uwagę na tekst etykietki narzędzia, który pojawia się po jej zatrzymaniu.

3. Naciśnij klawisze CTRL + F, aby otworzyć okno dialogowe **Znajdowanie** .

4. W polu **Znajdź** , wpisz tekst zanotowany w kroku 2.

5. Sprawdź, czy **wszystkie otwarte dokumenty** są wyświetlane w polu **Szukaj w** .

6. Kliknij przycisk **Znajdź następny** do momentu wybrania tekstu w `<Strings>` sekcji [elementu Button](../../extensibility/button-element.md).

    `<Button>`Element, w którym pojawia się polecenie, jest definicją polecenia.

   Po znalezieniu definicji polecenia można umieścić kopię polecenia w innym menu lub pasku narzędzi, tworząc [element CommandPlacement](../../extensibility/commandplacement-element.md) , który ma takie same `guid` wartości, `id` jak polecenie. Aby uzyskać więcej informacji, zobacz [Tworzenie grup przycisków do wielokrotnego użytku](../../extensibility/creating-reusable-groups-of-buttons.md).

### <a name="special-cases"></a>Specjalne przypadki
 W następujących przypadkach tekst menu lub etykietka narzędzia mogą nie być dokładnie zgodne z definicją polecenia.

- Elementy menu, które zawierają podkreślony znak, taki jak polecenie **Print** w menu **plik** , w którym P jest podkreślony.

     Znaki poprzedzone znakiem "&" w nazwach elementów menu są wyświetlane jako podkreślone. Jednak pliki. vsct są napisane w języku XML, który używa znaku "&", aby wskazać znaki specjalne i wymaga, aby element "", który ma być wyświetlany, musi być wpisany jako " &amp; ". W związku z tym w pliku. vsct polecenie **Print** pojawia się jako " &amp; Print".

- Polecenia, które mają dynamiczny tekst, takie jak **Zapisz** *bieżącą nazwę pliku*i dynamicznie generowane elementy menu, takie jak elementy na liście **ostatnie pliki** .

     Nie istnieje niezawodny sposób wyszukiwania tekstu dynamicznego. Zamiast tego Znajdź grupę, która hostuje odpowiednie polecenie, sprawdzając identyfikatory [GUID i identyfikatory menu programu Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) lub identyfikatorów [GUID i identyfikatory pasków narzędzi programu Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md), a następnie wyszukaj identyfikator tej grupy. Jeśli definicja polecenia nie ma grupy jako [elementu nadrzędnego](../../extensibility/parent-element.md), Wyszukaj SharedCmdPlace. vsct i ShellCmdPlace. vsct (lub VsDbgCmdPlace. vsct dla poleceń debugera) dla `<CommandPlacement>` elementu, który ustawia element nadrzędny polecenia. SharedCmdPlace. vsct, ShellCmdPlace. vsct, andVsDbgCmdPlace. vsct, znajdują się w folderze *ścieżka instalacji zestawu Visual Studio SDK*\VisualStudioIntegration\Common\Inc\.

## <a name="see-also"></a>Zobacz też
 [MenuCommands a OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md) — [tabela poleceń programu Visual Studio (. Vsct) pliki](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) [vsct dokumentacja schematu XML](../../extensibility/vsct-xml-schema-reference.md)
