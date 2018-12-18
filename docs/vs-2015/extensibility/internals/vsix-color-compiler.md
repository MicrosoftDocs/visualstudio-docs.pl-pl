---
title: Kompilator kolorów VSIX | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 99395da7-ec34-491d-9baa-0590d23283ce
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 19ca749b3ddd2190fd667ddb6c96c2a88c557999
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51788436"
---
# <a name="vsix-color-compiler"></a>Kompilator kolorów VSIX
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Narzędzie kompilatora kolor rozszerzeń programu Visual Studio jest aplikację konsolową, która przyjmuje plik XML reprezentujący kolorów dla istniejących kompozycji programu Visual Studio i konwertuje je do .pkgdef plików tak, aby te kolory mogą być używane w programie Visual Studio. Ponieważ jest to łatwe porównywanie różnic między plikami XML to narzędzie jest przydatne w celu zarządzania kolorów niestandardowych w kontroli źródła. On również mogą być dołączane do środowisk kompilacji tak, aby dane wyjściowe kompilacji, plik .pkgdef prawidłowe.  
  
 **Schemat XML motywu**  
  
 Plik XML motywu pełną wygląda następująco:  
  
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
  
 \<Motyw > element definiuje całego motywu. Motyw musi zawierać co najmniej jeden \<kategorii > element. Elementy motywu definiuje się następująco:  
  
```xml  
<Theme Name="name" GUID="guid">  
      <!-- one or more Category elements -->  
</Theme>  
```  
  
|||  
|-|-|  
|**Atrybut**|**Definicja**|  
|Nazwa|[Wymagane] Nazwa motywu|  
|Identyfikator GUID|[Wymagane] Identyfikator GUID motywu (musi być identyfikatorem GUID formatowanie)|  
  
 Podczas tworzenia niestandardowych kolorów dla programu Visual Studio, te kolory muszą być zdefiniowane dla następujących tematów. Jeśli kolory nie istnieje dla wybranego motywu, Visual Studio próbuje załadować brakujących kolorów z motyw jasny.  
  
|||  
|-|-|  
|**Nazwa motywu**|**Motyw identyfikatora GUID**|  
|Światła|{de3dbbcd-f642-433c-8353-8f1df4370aba}|  
|Ciemny|{1ded0138-47ce-435e-84ef-9ec1f439b749}|  
|Niebieski|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|  
|Duży kontrast|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|  
  
 **Kategoria**  
  
 \<Kategorii > element definiuje zbiór kolory motywu. Nazwy kategorii zapewniają logiczne grupowanie i powinien być zdefiniowany jako wąskiego, jak to możliwe. Kategoria musi zawierać co najmniej jeden \<kolor > element. Kategoria, elementy są zdefiniowane następująco:  
  
```xml  
<Category Name="name" GUID="guid">  
      <!-- one or more Color elements -->  
 </Category>  
```  
  
|||  
|-|-|  
|**Atrybut**|**Definicja**|  
|Nazwa|[Wymagane] Nazwa kategorii|  
|Identyfikator GUID|[Wymagane] Identyfikator GUID kategorii (musi być identyfikatorem GUID formatowanie)|  
  
 **Kolor**  
  
 \<Kolor > element Określa kolor dla składnika lub stan interfejsu użytkownika. Preferowany schemat nazewnictwa dla koloru jest [typ interfejsu użytkownika] [Stan]. Nie należy używać słowa "pole color", ponieważ jest nadmiarowy. Kolor musi wyraźnie określać typ elementu i sytuacji lub "stan", dla których zostaną zastosowane kolor. Kolor, który nie może być pusta i musi zawierać jedną lub obie \<tła > i \<pierwszego planu > element. Kolor elementów są zdefiniowane następująco:  
  
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
  
 \<Tła > i \<pierwszego planu > elementy Zdefiniuj kolor, który wartość i typ dla tła lub pierwszy plan elementu interfejsu użytkownika. Elementy te nie mają elementów podrzędnych.  
  
```xml  
<Background Type="type" Source="int" />  
<Foreground Type="type" Source="int" />  
```  
  
|||  
|-|-|  
|**Atrybut**|**Definicja**|  
|Typ|[Wymagane] Typ koloru. Może to być jedna z następujących czynności:<br /><br /> *CT_INVALID:* kolor jest nieprawidłowy lub nie została ustawiona.<br /><br /> *CT_RAW:* nieprzetworzonej wartości ARGB.<br /><br /> *CT_COLORINDEX:* NIE NALEŻY UŻYWAĆ.<br /><br /> *CT_SYSCOLOR:* kolor systemu Windows na podstawie SysColor.<br /><br /> *CT_VSCOLOR:* koloru programu Visual Studio z __VSSYSCOLOREX.<br /><br /> *CT_AUTOMATIC:* kolorowi automatycznemu.<br /><br /> *CT_TRACK_FOREGROUND:* NIE NALEŻY UŻYWAĆ.<br /><br /> *CT_TRACK_BACKGROUND:* NIE NALEŻY UŻYWAĆ.|  
|Źródło|[Wymagane] Wartość koloru reprezentowane w formacie szesnastkowym|  
  
 Obsługiwane przez wyliczenie __VSCOLORTYPE wszystkie wartości są obsługiwane przez schemat w atrybucie typu. Jednak zaleca się, że można używać tylko CT_RAW i CT_SYSCOLOR.  
  
 **Wszystko w jednym**  
  
 Jest to prosty przykład pliku XML motywu są prawidłowe:  
  
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
  
 VsixColorCompiler \<pliku XML > \<pliku PkgDef > \<argumentów opcjonalnych >  
  
 **Argumenty**  
  
||||  
|-|-|-|  
|**Nazwa przełącznika**|**Uwagi**|**Wymagane lub opcjonalne**|  
|Nienazwane (plik XML)|To jest pierwszy parametr nienazwany i ścieżkę do pliku XML do konwersji.|Wymagane|  
|Nienazwane (plik .pkgdef)|To jest drugi parametr bez nazwy i ścieżki wyjściowej dla pliku .pkgdef wygenerowany.<br /><br /> Wartość domyślna: \<XML, nazwa_pliku > .pkgdef|Optional|  
|/ nologo|Ustawienie tej flagi powoduje zatrzymanie produktu i praw autorskich informacje dotyczące drukowania.|Optional|  
|/?|Wydrukuj informacje pomocy.|Optional|  
|/help|Wydrukuj informacje pomocy.|Optional|  
  
 **Przykłady**  
  
-   D:\pkgdef\colors.pkgdef VsixColorCompiler D:\xml\colors.xml  
  
-   / Nologo VsixColorCompiler D:\xml\colors.xml  
  
## <a name="notes"></a>Uwagi  
  
-   To narzędzie wymaga zainstalowania najnowszej wersji środowiska uruchomieniowego VC ++.  
  
-   Obsługiwane są tylko pojedynczych plików. Konwersja zbiorcza za pośrednictwem ścieżek folderów nie jest obsługiwana.  
  
## <a name="sample-output"></a>Przykładowe dane wyjściowe  
 Plik .pkgdef wygenerowany przez narzędzie będą podobne do poniższych kluczy:  
  
```  
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\Environment]  
"Data"=hex:3a,00,00,00,0b,00,00,00,01,00,00,00,c3,d9,4e,62,fd,bd,fa,41,96,c3,7c,82,4e,a3,2e,3d,01,00,00,00,0c,00,00,00,41,63,74,69,76,65,42,6f,72,64,65,72,01,cc,ce,db,ff,01,33,31,24,ff  
  
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\TreeView]  
"Data"=hex:38,00,00,00,0b,00,00,00,01,00,00,00,8e,f0,ec,92,13,8b,f4,4c,99,e9,ae,26,92,38,21,85,01,00,00,00,0a,00,00,00,42,61,63,6b,67,72,6f,75,6e,64,01,f5,f5,f5,ff,01,1e,1e,1e,ff  
```

