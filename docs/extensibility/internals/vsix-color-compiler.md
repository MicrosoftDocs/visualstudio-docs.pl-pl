---
title: Kompilator kolorów VSIX | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 99395da7-ec34-491d-9baa-0590d23283ce
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f414a56bb05a23b6efef19aa7c99292b8a40038a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703904"
---
# <a name="vsix-color-compiler"></a>Kompilator kolorów VSIX
Narzędzie Visual Studio Extension Color Compiler to aplikacja konsoli, która pobiera plik xml reprezentujący kolory dla istniejących motywów programu Visual Studio i zakrywa go do pliku pkgdef, dzięki czemu te kolory mogą być używane w programie Visual Studio. Ponieważ można łatwo porównać różnice między plikami xml, to narzędzie jest przydatne do zarządzania niestandardowymi kolorami w kontroli źródła. Można również podłączyć do środowisk kompilacji, tak aby dane wyjściowe kompilacji jest prawidłowy plik pkgdef.

 **Schemat XML motywu**

 Kompletny motyw .xml plik wygląda następująco:

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

 **motyw**

 Element \<> motywu definiuje cały motyw. Motyw musi zawierać co \<najmniej jeden element kategorii>. Elementy motywu są zdefiniowane w ten sposób:

```xml
<Theme Name="name" GUID="guid">
      <!-- one or more Category elements -->
</Theme>
```

|||
|-|-|
|**Atrybut**|**Definicja**|
|Nazwa|[Wymagane] Nazwa motywu|
|Identyfikator GUID|[Wymagane] Identyfikator GUID motywu (musi być zgodny z formatowaniem GUID)|

 Podczas tworzenia niestandardowych kolorów programu Visual Studio te kolory muszą być zdefiniowane dla następujących motywów. Jeśli dla określonego motywu nie istnieją żadne kolory, program Visual Studio próbuje załadować brakujące kolory z motywu Światło.

|||
|-|-|
|**Nazwa motywu**|**Identyfikator GUID motywu**|
|Jasny|{de3dbbcd-f642-433c-8353-8f1df4370aba}|
|Ciemny|{1ded0138-47ce-435e-84ef-9ec1f439b749}|
|Blue|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|
|Wysoki kontrast|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|

 **Kategoria**

 Element \<kategoria> definiuje kolekcję kolorów w motywie. Nazwy kategorii zapewniają logiczne grupowania i powinny być definiowane tak wąsko, jak to możliwe. Kategoria musi zawierać co \<najmniej jeden element Color>. Elementy kategorii są zdefiniowane w ten sposób:

```xml
<Category Name="name" GUID="guid">
      <!-- one or more Color elements -->
 </Category>
```

|||
|-|-|
|**Atrybut**|**Definicja**|
|Nazwa|[Wymagane] Nazwa kategorii|
|Identyfikator GUID|[Wymagane] Identyfikator GUID kategorii (musi być zgodny z formatowaniem GUID)|

 **Kolor**

 Element \<Color> definiuje kolor dla komponentu lub stanu interfejsu użytkownika. Preferowanym schematem nazewnictwa dla koloru jest [Typ interfejsu użytkownika] [Stan]. Nie należy używać słowa "kolor", ponieważ jest ono zbędne. Kolor powinien wyraźnie wskazywać typ elementu i sytuacje lub "stan", dla którego zostanie zastosowany kolor. Kolor nie może być pusty i musi zawierać jeden \<lub oba> \<tła i pierwszego planu> element. Elementy kolorów są zdefiniowane w ten sposób:

```xml
<Color Name="name">
        <Background /> <!-- zero or one Background element -->
        <Foreground /> <!-- zero or one Foreground element -->
 </Color>
```

|||
|-|-|
|**Atrybut**|**Definicja**|
|Nazwa|[Wymagane] Nazwa koloru|

 **Tło i/lub pierwszy plan**

 Elementy \<> tła \<i pierwszego planu> definiują wartość i typ koloru dla tła lub pierwszego planu elementu interfejsu użytkownika. Elementy te nie mają dzieci.

```xml
<Background Type="type" Source="int" />
<Foreground Type="type" Source="int" />
```

|||
|-|-|
|**Atrybut**|**Definicja**|
|Typ|[Wymagane] Typ koloru. Może to być jedna z następujących czynności:<br /><br /> *CT_INVALID:* Kolor jest nieprawidłowy lub nie jest ustawiony.<br /><br /> *CT_RAW:* Nieprzetworzona wartość ARGB.<br /><br /> *CT_COLORINDEX:* NIE UŻYWAĆ.<br /><br /> *CT_SYSCOLOR:* Kolor systemu Windows firmy SysColor.<br /><br /> *CT_VSCOLOR:* Kolor programu Visual Studio z __VSSYSCOLOREX.<br /><br /> *CT_AUTOMATIC:* Kolor automatyczny.<br /><br /> *CT_TRACK_FOREGROUND:* NIE UŻYWAĆ.<br /><br /> *CT_TRACK_BACKGROUND:* NIE UŻYWAĆ.|
|Element źródłowy|[Wymagane] Wartość koloru reprezentowanego w szesnastkowym|

 Wszystkie wartości obsługiwane przez wyliczenie __VSCOLORTYPE są obsługiwane przez schemat w atrybutu Type. Zalecamy jednak używanie tylko CT_RAW i CT_SYSCOLOR.

 **Wszystko razem**

 Jest to prosty przykład prawidłowego pliku xml motywu:

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
 **Składni**

 VsixColorCompiler \<plik XML> \<plik PkgDef> \<opcjonalne Args>

 **Argumenty**

||||
|-|-|-|
|**Zmień nazwę**|**Uwagi**|**Wymagane lub opcjonalne**|
|Bez nazwy (plik xml)|Jest to pierwszy nienazwany parametr i jest ścieżką do pliku XML do konwersji.|Wymagany|
|Bez nazwy (plik pkgdef)|Jest to drugi nienazwany parametr i jest ścieżką wyjściową dla wygenerowanego pliku pkgdef.<br /><br /> Domyślnie: \<Nazwa pliku XML>.pkgdef|Optional (Opcjonalność)|
|/noLogo|Ustawienie tej flagi uniemożliwia drukowanie informacji o produktach i prawach autorskich.|Optional (Opcjonalność)|
|/?|Wydrukuj informacje o Pomocy.|Optional (Opcjonalność)|
|/help|Wydrukuj informacje o Pomocy.|Optional (Opcjonalność)|

 **Przykłady**

- VsixColorCompiler D:\xml\colors.xml D:\pkgdef\colors.pkgdef

- VsixColorCompiler D:\xml\colors.xml /noLogo

## <a name="notes"></a>Uwagi

- To narzędzie wymaga zainstalowania najnowszej wersji środowiska wykonawczego VC++.

- Obsługiwane są tylko pojedyncze pliki. Konwersja zbiorcza za pośrednictwem ścieżek folderów nie jest obsługiwana.

## <a name="sample-output"></a>Przykładowe dane wyjściowe
 Plik .pkgdef wygenerowany przez narzędzie będzie podobny do poniższych klawiszy:

```
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\Environment]
"Data"=hex:3a,00,00,00,0b,00,00,00,01,00,00,00,c3,d9,4e,62,fd,bd,fa,41,96,c3,7c,82,4e,a3,2e,3d,01,00,00,00,0c,00,00,00,41,63,74,69,76,65,42,6f,72,64,65,72,01,cc,ce,db,ff,01,33,31,24,ff

[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\TreeView]
"Data"=hex:38,00,00,00,0b,00,00,00,01,00,00,00,8e,f0,ec,92,13,8b,f4,4c,99,e9,ae,26,92,38,21,85,01,00,00,00,0a,00,00,00,42,61,63,6b,67,72,6f,75,6e,64,01,f5,f5,f5,ff,01,1e,1e,1e,ff
```
