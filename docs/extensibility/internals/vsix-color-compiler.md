---
title: VsIX Color Compiler | Microsoft Docs
description: Dowiedz się więcej Visual Studio kompilatora kolorów rozszerzenia, czyli aplikacji konsolowej, która zakrywa kolory Visual Studio motywach do pliku pkgdef.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 99395da7-ec34-491d-9baa-0590d23283ce
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2f7277299d3cedd2ea0db49a44109d8a0441ebd0
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901763"
---
# <a name="vsix-color-compiler"></a>Kompilator kolorów VSIX
Narzędzie Visual Studio Extension Color Compiler to aplikacja konsolowa, która pobiera plik .xml reprezentujący kolory istniejących motywów Visual Studio i zakrywa go do pliku pkgdef, dzięki czemu te kolory mogą być używane w Visual Studio. Ponieważ można łatwo porównać różnice między plikami .xml, to narzędzie jest przydatne do zarządzania kolorami niestandardowymi w kontroli źródła. Można go również podłączyć do środowisk kompilacji, tak aby dane wyjściowe kompilacji było prawidłowym plikiem pkgdef.

 **Schemat XML motywu**

 Pełny motyw .xml wygląda następująco:

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

 Element \<Theme> definiuje cały motyw. Motyw musi zawierać co najmniej jeden \<Category> element. Elementy motywu są zdefiniowane w ten sposób:

```xml
<Theme Name="name" GUID="guid">
      <!-- one or more Category elements -->
</Theme>
```

|**Atrybut**|**Definicja**|
|-|-|
|Nazwa|[Wymagane] Nazwa motywu|
|GUID|[Wymagane] Identyfikator GUID motywu (musi być zgodne z formatowaniem identyfikatora GUID)|

 Podczas tworzenia niestandardowych kolorów Visual Studio te kolory muszą być zdefiniowane dla następujących motywów. Jeśli dla określonego motywu nie ma kolorów, Visual Studio załadować brakujące kolory z motywu Jasny.

|**Nazwa motywu**|**Identyfikator GUID motywu**|
|-|-|
|Jasny|{de3dbbcd-f642-433c-8353-8f1df4370aba}|
|Ciemny|{1ded0138-47ce-435e-84ef-9ec1f439b749}|
|Blue (Niebieski)|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|
|duży kontrast|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|

 **Kategoria**

 Element \<Category> definiuje kolekcję kolorów w motywie. Nazwy kategorii zapewniają logiczne grupowania i powinny być zdefiniowane tak wąsko, jak to możliwe. Kategoria musi zawierać co najmniej jeden \<Color> element. Elementy kategorii są zdefiniowane w ten sposób:

```xml
<Category Name="name" GUID="guid">
      <!-- one or more Color elements -->
 </Category>
```

|**Atrybut**|**Definicja**|
|-|-|
|Nazwa|[Wymagane] Nazwa kategorii|
|GUID|[Wymagane] Identyfikator GUID kategorii (musi być zgodne z formatowaniem identyfikatora GUID)|

 **Kolor**

 Element definiuje kolor składnika lub stanu \<Color> interfejsu użytkownika. Preferowany schemat nazewnictwa koloru to [typ interfejsu użytkownika] [Stan]. Nie używaj słowa "color", ponieważ jest ono nadmiarowe. Kolor powinien wyraźnie wskazywać typ elementu i sytuacje, czyli "stan", dla którego zostanie zastosowany kolor. Kolor nie może być pusty i musi zawierać jeden lub oba elementy \<Background> \<Foreground> i . Elementy koloru są zdefiniowane w ten sposób:

```xml
<Color Name="name">
        <Background /> <!-- zero or one Background element -->
        <Foreground /> <!-- zero or one Foreground element -->
 </Color>
```

|**Atrybut**|**Definicja**|
|-|-|
|Nazwa|[Wymagane] Nazwa koloru|

 **Tło i/lub pierwszy plan**

 Elementy i definiują wartość i typ koloru dla tła lub pierwszego planu \<Background> \<Foreground> elementu interfejsu użytkownika. Te elementy nie mają elementów children.

```xml
<Background Type="type" Source="int" />
<Foreground Type="type" Source="int" />
```

|**Atrybut**|**Definicja**|
|-|-|
|Typ|[Wymagane] Typ koloru. Może to być jedna z następujących opcji:<br /><br /> *CT_INVALID:* Kolor jest nieprawidłowy lub nie został ustawiony.<br /><br /> *CT_RAW:* Nieprzetworzone wartości ARGB.<br /><br /> *CT_COLORINDEX:* NIE UŻYWAJ.<br /><br /> *CT_SYSCOLOR:* Kolor systemu Windows z SysColor.<br /><br /> *CT_VSCOLOR:* Kolor Visual Studio z __VSSYSCOLOREX.<br /><br /> *CT_AUTOMATIC:* Kolor automatyczny.<br /><br /> *CT_TRACK_FOREGROUND:* NIE UŻYWAJ.<br /><br /> *CT_TRACK_BACKGROUND:* NIE UŻYWAJ.|
|Element źródłowy|[Wymagane] Wartość koloru reprezentowanego w wartości szesnastkowej|

 Wszystkie wartości obsługiwane przez __VSCOLORTYPE są obsługiwane przez schemat w atrybutze Type. Zalecamy jednak używanie tylko tych CT_RAW i CT_SYSCOLOR.

 **Wszystkie razem**

 Jest to prosty przykład prawidłowego motywu .xml pliku:

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
|Nienazwane (.xml pliku)|Jest to pierwszy parametr bez nazwy i jest ścieżką do pliku XML do przekonwertowania.|Wymagane|
|Bez nazwy (plik pkgdef)|Jest to drugi parametr bez nazwy i jest ścieżką wyjściową wygenerowanego pliku pkgdef.<br /><br /> Ustawienie domyślne: \<XML Filename> .pkgdef|Opcjonalne|
|/noLogo|Ustawienie tej flagi zatrzymuje drukowanie informacji o produkcie i prawach autorskich.|Opcjonalne|
|/?|Wydrukuj informacje o Pomocy.|Opcjonalne|
|/help|Wydrukuj informacje o Pomocy.|Opcjonalne|

 **Przykłady**

- VsixColorCompiler D:\xml\colors.xml D:\pkgdef\colors.pkgdef

- VsixColorCompiler D:\xml\colors.xml /noLogo

## <a name="notes"></a>Uwagi

- To narzędzie wymaga zainstalowania najnowszej wersji środowiska uruchomieniowego VC++.

- Obsługiwane są tylko pojedyncze pliki. Konwersja zbiorcza za pośrednictwem ścieżek folderów nie jest obsługiwana.

- Narzędzie można znaleźć w `<VS Install Path>\VSSDK\VisualStudioIntegration\Tools\Bin\`

## <a name="sample-output"></a>Przykładowe dane wyjściowe
 Plik pkgdef wygenerowany przez narzędzie będzie podobny do poniższych kluczy:

```
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\Environment]
"Data"=hex:3a,00,00,00,0b,00,00,00,01,00,00,00,c3,d9,4e,62,fd,bd,fa,41,96,c3,7c,82,4e,a3,2e,3d,01,00,00,00,0c,00,00,00,41,63,74,69,76,65,42,6f,72,64,65,72,01,cc,ce,db,ff,01,33,31,24,ff

[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\TreeView]
"Data"=hex:38,00,00,00,0b,00,00,00,01,00,00,00,8e,f0,ec,92,13,8b,f4,4c,99,e9,ae,26,92,38,21,85,01,00,00,00,0a,00,00,00,42,61,63,6b,67,72,6f,75,6e,64,01,f5,f5,f5,ff,01,1e,1e,1e,ff
```
