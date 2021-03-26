---
title: Kompilator kolorów VSIX | Microsoft Docs
description: Dowiedz się więcej o narzędziu kompilatora kolorów rozszerzenia programu Visual Studio, która jest aplikacją konsolową, która umożliwia przeciąganie kolorów w motywach programu Visual Studio do pliku pkgdef.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 99395da7-ec34-491d-9baa-0590d23283ce
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9486f1cd3e931d134c6fe2842f8704926de70966
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105060708"
---
# <a name="vsix-color-compiler"></a>Kompilator kolorów VSIX
Visual Studio Extension Color Tool narzędzie kompilatora to Aplikacja konsolowa, która pobiera plik. XML reprezentujący kolory dla istniejących motywów programu Visual Studio i dzieli go na plik. pkgdef, dzięki czemu można używać tych kolorów w programie Visual Studio. Ponieważ można łatwo porównać różnice między plikami XML, to narzędzie jest przydatne do zarządzania kolorami niestandardowymi w kontroli źródła. Można go również podłączyć do środowisk kompilacji, aby dane wyjściowe kompilacji były prawidłowym plikiem. pkgdef.

 **Schemat XML motywu**

 Kompletny plik Theme. XML wygląda następująco:

```xml
<Themes>
      <!—one or Theme elements -->
      <Theme>
        <!-- one or more Category elements -->
        <Category>
          <!-- one or more Color elements -->
          <Color>
            <!-- zero or one Background element -->
            <Background />
            <!-- zero or one Foreground element -->
            <Foreground />
          </Color>
        </Category>
      </Theme>
</Themes>
```

 **Motyw**

 \<Theme>Element definiuje cały motyw. Motyw musi zawierać co najmniej jeden \<Category> element. Elementy motywu są zdefiniowane w następujący sposób:

```xml
<Theme Name="name" GUID="guid">
      <!-- one or more Category elements -->
</Theme>
```

|**Atrybut**|**Definicja**|
|-|-|
|Nazwa|Potrzeb Nazwa motywu|
|GUID|Potrzeb Identyfikator GUID motywu (musi być zgodny z formatowaniem identyfikatora GUID)|

 Podczas tworzenia niestandardowych kolorów dla programu Visual Studio należy zdefiniować te kolory dla następujących motywów. Jeśli nie istnieją żadne kolory dla określonego motywu, program Visual Studio próbuje załadować brakujące kolory z motywu jasne.

|**Nazwa motywu**|**Identyfikator GUID motywu**|
|-|-|
|Jasny|{de3dbbcd-f642-433c-8353-8f1df4370aba}|
|Ciemny|{1ded0138-47ce-435e-84ef-9ec1f439b749}|
|Blue (Niebieski)|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|
|duży kontrast|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|

 **Kategoria**

 \<Category>Element definiuje zbiór kolorów w motywie. Nazwy kategorii zapewniają logiczne grupowania i powinny być zdefiniowane w możliwie najwęższy sposób. Kategoria musi zawierać co najmniej jeden \<Color> element. Elementy kategorii są zdefiniowane w następujący sposób:

```xml
<Category Name="name" GUID="guid">
      <!-- one or more Color elements -->
 </Category>
```

|**Atrybut**|**Definicja**|
|-|-|
|Nazwa|Potrzeb Nazwa kategorii|
|GUID|Potrzeb Identyfikator GUID kategorii (musi być zgodny z formatowaniem identyfikatora GUID)|

 **Kolor**

 \<Color>Element definiuje kolor składnika lub stanu interfejsu użytkownika. Preferowanym schematem nazewnictwa dla koloru jest [typ interfejsu użytkownika] [stan]. Nie używaj słowa "Color", ponieważ jest ono nadmiarowe. Kolor powinien jasno wskazywać typ elementu i sytuacje, lub "stan", do którego zostanie zastosowany kolor. Kolor nie może być pusty ani zawierać jednego lub obu \<Background> \<Foreground> elementów i. Elementy koloru są zdefiniowane w następujący sposób:

```xml
<Color Name="name">
        <Background /> <!-- zero or one Background element -->
        <Foreground /> <!-- zero or one Foreground element -->
 </Color>
```

|**Atrybut**|**Definicja**|
|-|-|
|Nazwa|Potrzeb Nazwa koloru|

 **Tło i/lub pierwszy plan**

 \<Background>Elementy i \<Foreground> definiują wartość koloru i typ dla tła lub pierwszego planu elementu interfejsu użytkownika. Te elementy nie mają żadnych elementów podrzędnych.

```xml
<Background Type="type" Source="int" />
<Foreground Type="type" Source="int" />
```

|**Atrybut**|**Definicja**|
|-|-|
|Typ|Potrzeb Typ koloru. Może to być jedna z następujących opcji:<br /><br /> *CT_INVALID:* Kolor jest nieprawidłowy lub nie został ustawiony.<br /><br /> *CT_RAW:* Pierwotna wartość ARGB.<br /><br /> *CT_COLORINDEX:* NIE NALEŻY UŻYWAĆ.<br /><br /> *CT_SYSCOLOR:* Kolor systemu Windows z SysColor.<br /><br /> *CT_VSCOLOR:* Kolor programu Visual Studio z __VSSYSCOLOREX.<br /><br /> *CT_AUTOMATIC:* Kolor automatyczny.<br /><br /> *CT_TRACK_FOREGROUND:* NIE NALEŻY UŻYWAĆ.<br /><br /> *CT_TRACK_BACKGROUND:* NIE NALEŻY UŻYWAĆ.|
|Element źródłowy|Potrzeb Wartość koloru reprezentowanego w formacie szesnastkowym|

 Wszystkie wartości obsługiwane przez Wyliczenie __VSCOLORTYPE są obsługiwane przez schemat w atrybucie typu. Zaleca się jednak używanie tylko CT_RAW i CT_SYSCOLOR.

 **Wszystkie razem**

 Jest to prosty przykład prawidłowego pliku Theme. XML:

```xml
<Themes>
  <Theme Name="Light" GUID="{de3dbbcd-f642-433c-8353-8f1df4370aba}">
    <Category Name="MyCategory" GUID="{0A96238B-70CE-4479-9170-EECEAA3FCD58}">
      <Color Name="MyActiveBorder">
        <Background Type="CT_RAW" Source="FFCCCEDB" />
      </Color>
    </Category>
  </Theme>
</Themes>
```

## <a name="how-to-use-the-tool"></a>Jak korzystać z narzędzia
 **Składnia**

 VsixColorCompiler \<XML file> \<PkgDef file>\<Optional Args>

 **Argumenty**

|**Nazwa przełącznika**|**Uwagi**|**Wymagane lub opcjonalne**|
|-|-|-|
|Bez nazwy (plik. xml)|Jest to pierwszy parametr bez nazwy i jest ścieżką do pliku XML do przekonwertowania.|Wymagane|
|Bez nazwy (plik. pkgdef)|Jest to drugi nienazwany parametr, który jest ścieżką wyjściową wygenerowanego pliku pkgdef.<br /><br /> Wartość domyślna: \<XML Filename> . pkgdef|Opcjonalne|
|/noLogo|Ustawienie tej flagi uniemożliwia drukowanie informacji o produkcie i prawach autorskich.|Opcjonalne|
|/?|Drukuj informacje pomocy.|Opcjonalne|
|/help|Drukuj informacje pomocy.|Opcjonalne|

 **Przykłady**

- VsixColorCompiler D:\xml\colors.xml D:\pkgdef\colors.pkgdef

- VsixColorCompiler D:\xml\colors.xml/noLogo

## <a name="notes"></a>Uwagi

- To narzędzie wymaga zainstalowania najnowszej wersji środowiska uruchomieniowego VC + +.

- Obsługiwane są tylko pojedyncze pliki. Konwersja zbiorcza przez ścieżki folderów nie jest obsługiwana.

## <a name="sample-output"></a>Przykładowe dane wyjściowe
 Plik. pkgdef wygenerowany przez narzędzie będzie wyglądać podobnie do poniższego klucza:

```
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\Environment]
"Data"=hex:3a,00,00,00,0b,00,00,00,01,00,00,00,c3,d9,4e,62,fd,bd,fa,41,96,c3,7c,82,4e,a3,2e,3d,01,00,00,00,0c,00,00,00,41,63,74,69,76,65,42,6f,72,64,65,72,01,cc,ce,db,ff,01,33,31,24,ff

[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\TreeView]
"Data"=hex:38,00,00,00,0b,00,00,00,01,00,00,00,8e,f0,ec,92,13,8b,f4,4c,99,e9,ae,26,92,38,21,85,01,00,00,00,0a,00,00,00,42,61,63,6b,67,72,6f,75,6e,64,01,f5,f5,f5,ff,01,1e,1e,1e,ff
```
