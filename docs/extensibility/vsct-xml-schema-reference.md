---
title: Informacje o schemacie XML VSCT | Microsoft Docs
description: Artykuły referencyjne dotyczące schematu XML VSCT opisują elementy schematu kompilatora tabel poleceń z dozwolonymi elementami podrzędnymi i atrybutami dla każdego z nich.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Visual Studio command table configuration files (VSCT), XML schema
- VSCT XML schema elements
ms.assetid: 49e7efae-e713-4762-a824-96fdaf92cdc9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7d82cda9c91642b094deea50eda02676f9bb73f3
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905231"
---
# <a name="vsct-xml-schema-reference"></a>Odwołanie do schematu XML VSCT
Zawiera tabelę elementów schematu kompilatora tabel poleceń z dozwolonymi elementami podrzędnymi i atrybutami dla każdego z nich.

 Plik tabeli poleceń oparty na języku XML (vsct) definiuje elementy polecenia, które pakiet VSPackage udostępnia zintegrowanemu środowisku projektowemu (IDE). Te elementy obejmują elementy menu, menu, paski narzędzi i pola kombi.

> [!NOTE]
> Kompilator VSCT może uruchomić preprocesor w pliku vsct. Ponieważ jest to zazwyczaj preprocesor języka C++, można zdefiniować elementy includes i makra, które mają tę samą składnię, która jest używana w plikach języka C++. Przykłady można znaleźć w pliku vsct, który kreator Nowego projektu tworzy dla projektu VSPackage. 

## <a name="optional-elements"></a>Elementy opcjonalne
 Niektóre elementy VSCT są opcjonalne. Jeśli `Parent` argument nie zostanie określony, Group_Undefined:0 zostanie implikowana. Jeśli `Icon` argument nie zostanie określony, zostanie implikowany identyfikator guidOfficeIcon:msotcidNoIcon. Po zdefiniowanym klawiszu skrótu emulacja, która jest zwykle nieużywana, jest opcjonalna.

 Elementy mapy bitowej mogą być osadzane w czasie kompilacji, określając lokalizację paska mapy bitowej w `href` argumentie . Pasek mapy bitowej jest kopiowany podczas scalania, a nie wyodrębniony z zasobów biblioteki DLL. Po podano argument staje się opcjonalny, a wszystkie gniazda na pasku `href` `usedList` mapy bitowej są uznawane za używane.

 Wszystkie wartości identyfikatorów GUID i ID muszą być zdefiniowane przy użyciu nazw symbolicznych. Te nazwy mogą być zdefiniowane w plikach nagłówkowych lub w sekcjach \<Symbols> VSCT. Nazwy symboliczne muszą być lokalne, dołączone za \<Include> pośrednictwem elementów lub przywołyne przez \<Extern> elementy. Nazwa symboliczna jest importowana z pliku nagłówkowego określonego w elemencie, jeśli jest zgodna z prostym wzorcem elementu \<Extern> #define SYMBOL. Wartość może być innym symbolem, o ile ten symbol został wcześniej zdefiniowany. Definicje identyfikatorów GUID muszą być zgodne z formatem OLE lub C++. Wartości identyfikatorów mogą być cyframi dziesiętnych lub szesnastkowymi poprzedzonymi cyframi 0x, jak pokazano w następujących wierszach:

- {6D484634-E53D-4a2c-ADCB-55145C9362C8}

- { 0x6d484634, 0xe53d, 0x4a2c, { 0xad, 0xcb, 0x55, 0x14, 0x5c, 0x93, 0x62, 0xc8 } } }

  Komentarze XML mogą być używane, ale narzędzia graficznego interfejsu użytkownika (GUI) mogą je odrzucać. Zawartość elementów \<Annotation> musi być utrzymywana niezależnie od formatu.

## <a name="schema-hierarchy"></a>Hierarchia schematów
 Plik .vsct ma następujące główne elementy.

- [CommandTable, element](../extensibility/commandtable-element.md)

- [Extern, element](../extensibility/extern-element.md)

- [Include, element](../extensibility/include-element.md)

- [Define, element](../extensibility/define-element.md)

- [Commands, element](../extensibility/commands-element.md)

- [CommandPlacements, element](../extensibility/commandplacements-element.md)

- [VisibilityConstraints, element](../extensibility/visibilityconstraints-element.md)

- [KeyBindings, element](../extensibility/keybindings-element.md)

- [UsedCommands, element](../extensibility/usedcommands-element.md)

- [Element nadrzędny](../extensibility/parent-element.md)

- [Icon, element](../extensibility/icon-element.md)

- [Strings, element](../extensibility/strings-element.md)

- [Command Flag, element](../extensibility/command-flag-element.md)

- [Symbols, element](../extensibility/symbols-element.md)

- [Atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md)

## <a name="see-also"></a>Zobacz też
- [Jak pakiet VSPackages dodaje elementy interfejsu użytkownika](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Routing poleceń w pakietach VSPackage](../extensibility/internals/command-routing-in-vspackages.md)
