---
title: VSCT schematu XML — Odwołanie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- Visual Studio command table configuration files (VSCT), XML schema
- VSCT XML schema elements
ms.assetid: 49e7efae-e713-4762-a824-96fdaf92cdc9
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e56de828d3b357762da98cde3b9591033c6b5d19
ms.sourcegitcommit: fb8babf5cd72f1fc2f97ffe4ad7b62d91f325f61
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2020
ms.locfileid: "64805734"
---
# <a name="vsct-xml-schema-reference"></a>Odwołanie do schematu XML VSCT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zawiera tabelę elementów schematu kompilatora tabel poleceń z dozwolonymi elementami podrzędnymi i atrybutami dla każdego z nich.  
  
 Plik konfiguracji tabeli poleceń opartych na języku XML (. vsct) definiuje elementy poleceń, które pakietu VSPackage zapewnia zintegrowane środowisko programistyczne (IDE). Te elementy obejmują elementy menu, menu, paski narzędzi i pola kombi.  
  
> [!NOTE]
> Kompilator VSCT może uruchomić preprocesor w pliku. vsct. Ponieważ jest to zwykle Preprocesor języka C++, można zdefiniować dołączenia i makra, które mają tę samą składnię, która jest używana w plikach języka C++. Przykłady tego typu są podane w pliku. vsct, który Kreator **nowego projektu** tworzy dla projektu pakietu VSPackage.  
  
## <a name="optional-elements"></a>Elementy opcjonalne  
 Niektóre elementy VSCT są opcjonalne. Jeśli `Parent` argument nie jest określony, Group_Undefined: 0 będzie to implikowane. Jeśli `Icon` argument nie jest określony, guidOfficeIcon: msotcidNoIcon zostanie implikowany. Gdy jest zdefiniowany klawisz skrótu, emulacja, która jest zwykle nieużywana, jest opcjonalna.  
  
 Elementy mapy bitowej mogą być osadzone w czasie kompilacji, określając lokalizację paska mapy bitowej w `href` argumencie. Pasek mapy bitowej jest kopiowany podczas scalania, a nie wyodrębniany z zasobów biblioteki DLL. Gdy `href` argument jest podany, argument jest `usedList` opcjonalny, a wszystkie gniazda na pasku mapy bitowej są uważane za używane.  
  
 Wszystkie wartości identyfikatora GUID i identyfikatora muszą być zdefiniowane przy użyciu nazw symbolicznych. Te nazwy mogą być zdefiniowane w plikach nagłówkowych lub w \<Symbols> sekcjach VSCT. Nazwy symboliczne muszą być lokalne, dołączone do \<Include> elementów lub odwołaniami do \<Extern> elementów. Nazwa symboliczna jest zaimportowana z pliku nagłówkowego określonego w \<Extern> elemencie, jeśli jest zgodna z prostym wzorcem #define wartości symbolu. Wartość może być innym symbolem, o ile ten symbol został wcześniej zdefiniowany. Definicje identyfikatorów GUID muszą być zgodne z formatem OLE lub C++. Wartości identyfikatorów mogą być cyframi dziesiętnymi lub cyframi szesnastkowymi, które są poprzedzone 0x, jak pokazano w następujących wierszach:  
  
- {6D484634-E53D-4a2c-ADCB-55145C9362C8}  
  
- { 0x6d484634, 0xe53d, 0x4a2c, { 0xad, 0xcb, 0x55, 0x14, 0x5c, 0x93, 0x62, 0xc8 } }  
  
  Komentarze XML mogą być używane, ale narzędzia graficznego interfejsu użytkownika (GUI) mogą je odrzucić. Zawartość \<Annotation> elementów można zachować niezależnie od formatu.  
  
## <a name="schema-hierarchy"></a>Hierarchia schematu  
 Plik. vsct zawiera następujące elementy główne.  
  
 [CommandTable, element](../extensibility/commandtable-element.md)  
  
 [Extern, element](../extensibility/extern-element.md)  
  
 [Include, element](../extensibility/include-element.md)  
  
 [Define, element](../extensibility/define-element.md)  
  
 [Commands, element](../extensibility/commands-element.md)  
  
 [CommandPlacements, element](../extensibility/commandplacements-element.md)  
  
 [VisibilityConstraints, element](../extensibility/visibilityconstraints-element.md)  
  
 [KeyBindings, element](../extensibility/keybindings-element.md)  
  
 [UsedCommands, element](../extensibility/usedcommands-element.md)  
  
 [Element nadrzędny](../extensibility/parent-element.md)  
  
 [Icon, element](../extensibility/icon-element.md)  
  
 [Strings, element](../extensibility/strings-element.md)  
  
 [Command Flag, element](../extensibility/command-flag-element.md)  
  
 [Symbols, element](../extensibility/symbols-element.md)  
  
 [Atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Jak pakietów VSPackage Dodawanie elementów interfejsu użytkownika](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Routing poleceń w pakietach VSPackage](../extensibility/internals/command-routing-in-vspackages.md)
