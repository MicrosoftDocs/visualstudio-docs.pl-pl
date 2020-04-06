---
title: Odwołanie do schematu XML VSCT | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio command table configuration files (VSCT), XML schema
- VSCT XML schema elements
ms.assetid: 49e7efae-e713-4762-a824-96fdaf92cdc9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 923a0c4b64fcae3a409a2298d6d481f6e1bb14db
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697899"
---
# <a name="vsct-xml-schema-reference"></a>Odwołanie do schematu XML VSCT
Zawiera tabelę elementów schematu kompilatora tabeli poleceń z dozwolonymi elementami podrzędnymi i atrybutami dla każdego z nich.

 Plik konfiguracji tabeli poleceń oparty na języku XML (vsct) definiuje elementy poleceń, które vsPackage zapewnia zintegrowanemu środowisku programistycznemu (IDE). Elementy te obejmują elementy menu, menu, paski narzędzi i pola kombi.

> [!NOTE]
> Kompilator VSCT można uruchomić preprocesora w pliku vsct. Ponieważ jest to zazwyczaj preprocesor języka C++, można zdefiniować zawiera i makra, które mają taką samą składnię, która jest używana w plikach Języka C++. Przykłady tego znajdują się w pliku vsct, który kreator **nowego projektu** tworzy dla projektu VSPackage.

## <a name="optional-elements"></a>Elementy opcjonalne
 Niektóre elementy VSCT są opcjonalne. Jeśli `Parent` argument nie jest określony, Group_Undefined:0 będą dorozumiane. Jeśli `Icon` argument nie zostanie określony, guidOfficeIcon:msotcidNoIcon zostaną dorozumiane. Po zdefiniowaniu klawisza skrótu emulacja, która jest zazwyczaj nieużywane, jest opcjonalna.

 Elementy mapy bitowej mogą być osadzone w czasie kompilacji, określając `href` lokalizację paska mapy bitowej w argumie. Pasek mapy bitowej jest kopiowany podczas scalania, a nie wyodrębniany z zasobów biblioteki DLL. Po `href` podaniu argumentu `usedList` argument staje się opcjonalny, a wszystkie gniazda w pasku mapy bitowej są uważane za używane.

 Wszystkie wartości identyfikatorów GUID i identyfikatorów muszą być zdefiniowane przy użyciu nazw symbolicznych. Nazwy te mogą być zdefiniowane w \<plikach nagłówkowych lub w> sekcjach symbole VSCT. Nazwy symboliczne muszą być lokalne, zawarte za pośrednictwem \<Include> \<elementów lub odwołuje się extern> elementów. Nazwa symboliczna jest importowana z pliku \<nagłówka określonego w elemencie> Extern, jeśli jest zgodna z prostym wzorcem #define WARTOŚCI SYMBOL. Wartość może być innym symbolem, o ile ten symbol został wcześniej zdefiniowany. Definicje identyfikatorów GUID muszą być zgodne z formatem OLE lub C++. Wartości identyfikatorów mogą być cyframi dziesiętnymi lub sześciokątnymi, które są poprzedzone cyfrą 0x, jak pokazano w następujących wierszach:

- {6D484634-E53D-4a2c-ADCB-55145C9362C8}

- { 0x6d484634, 0xe53d, 0x4a2c, { 0xad, 0xcb, 0x55, 0x14, 0x5c, 0x93, 0x62, 0xc8 } }

  Mogą być używane komentarze XML, ale narzędzia graficznego interfejsu użytkownika w obie strony mogą je odrzucić. Zawartość \<adnotacji> elementy są gwarantowane do utrzymania niezależnie od formatu.

## <a name="schema-hierarchy"></a>Hierarchia schematów
 Plik .vsct ma następujące główne elementy.

- [Element CommandTable](../extensibility/commandtable-element.md)

- [Element Extern](../extensibility/extern-element.md)

- [Dołącz element](../extensibility/include-element.md)

- [Zdefiniuj element](../extensibility/define-element.md)

- [Element Polecenia](../extensibility/commands-element.md)

- [Element Połowisku](../extensibility/commandplacements-element.md)

- [Element VisibilityConstraints](../extensibility/visibilityconstraints-element.md)

- [Element KeyBindings](../extensibility/keybindings-element.md)

- [Element UsedCommands](../extensibility/usedcommands-element.md)

- [Element nadrzędny](../extensibility/parent-element.md)

- [Element ikony](../extensibility/icon-element.md)

- [Element ciągów](../extensibility/strings-element.md)

- [Element flagi polecenia](../extensibility/command-flag-element.md)

- [Symbole, element](../extensibility/symbols-element.md)

- [Atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md)

## <a name="see-also"></a>Zobacz też
- [Jak vspackages dodać elementy interfejsu użytkownika](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Routing poleceń w pakietach VSPackages](../extensibility/internals/command-routing-in-vspackages.md)
