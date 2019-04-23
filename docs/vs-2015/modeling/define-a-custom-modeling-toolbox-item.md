---
title: Definiowanie niestandardowego elementu przybornika modelowania | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending, customizing the toolbox
ms.assetid: a2463606-1100-40ac-97f3-5ba22ca47b7c
caps.latest.revision: 33
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: becc123cab729aff7d1306bb0ee13aee521444ec
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60105048"
---
# <a name="define-a-custom-modeling-toolbox-item"></a>Definiowanie niestandardowego elementu przybornika modelowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby ułatwić tworzenie elementu lub grupy elementów zgodnie ze wzorca, które są często używane, można dodać nowe narzędzia do przybornika modelowania diagramów w programie Visual Studio. Można rozpowszechniać następujące elementy przybornika do innych użytkowników programu Visual Studio.  
  
 Aby zobaczyć, które wersje programu Visual Studio obsługuje tę funkcję, zobacz [obsługiwana wersja dla narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Niestandardowe narzędzie tworzy jeden lub więcej nowych elementów na diagramie. Na przykład można utworzyć niestandardowe narzędzie do tworzenia elementów, takich jak te:  
  
- Pakiet jest połączony z profilu platformy .NET i klasy z stereotyp .NET.  
  
- Para klas połączone przez skojarzenie, aby reprezentować wzorzec obserwatora.  
  
> [!NOTE]
>  Ta metoda umożliwia tworzenie narzędzi elementów. Oznacza to można utworzyć narzędzia, które zostaną przeciągnięte z przybornika do diagramu. Nie można utworzyć narzędzia Łącznik.  
  
## <a name="DefineTool"></a> Definiowanie niestandardowego narzędzia modelowania  
  
#### <a name="to-define-a-custom-modeling-tool"></a>Aby zdefiniować narzędzie do modelowania niestandardowe  
  
1. Tworzenie diagramu UML, który zawiera element lub grupy elementów.  
  
    - Te elementy mogą mieć relacje między nimi i może mieć zależne elementy, takie jak porty, atrybuty, operacje lub numerów PIN.  
  
2. Zapisz diagram przy użyciu nazwy, który chcesz nadać nowe narzędzie. Na **pliku** menu, użyj **Zapisz... Jako**.  
  
3. W Eksploratorze Windows skopiuj pliki dwóch diagram do następujący folder lub podfolder:  
  
     *YourDocuments* **elementów przybornika Tools\Custom \Visual Studio\Architecture**  
  
    - Utwórz ten folder, jeśli jeszcze nie istnieje. Może być konieczne utworzenie ich obu **narzędzia architektury** i **elementy do przybornika niestandardowego**.  
  
    - Skopiuj oba pliki diagramu, jedną nazwą, która kończy się w "menu... **diagram**", a druga o nazwie, która kończy"... **diagram.layout**"  
  
    - Można wprowadzić dowolną liczbę niestandardowych narzędzi, jak chcesz. Diagram użycia jeden dla każdego narzędzia.  
  
4. (Opcjonalnie) Tworzenie **.tbxinfo** plików zgodnie z opisem w temacie [sposób definiowania właściwości niestandardowe narzędzia](#tbxinfo)i dodaj go do tego samego katalogu. Dzięki temu można zdefiniować ikonę przybornika, etykietki narzędzi i tak dalej.  
  
    - Pojedynczy **.tbxinfo** pliku może służyć do definiowania wielu narzędzi. Może odnosić się do plików diagramu, które znajdują się w jego podfolderach.  
  
5. Uruchom ponownie program Visual Studio. Dodatkowe narzędzia pojawi się w przyborniku dla odpowiedniego typu diagramu.  
  
### <a name="what-the-custom-tool-will-replicate"></a>Jakie będą replikowane narzędzie niestandardowe  
 Narzędzie niestandardowe będą replikowane większość funkcji diagramu źródłowego:  
  
- Nazwy. Po utworzeniu elementu z przybornika do jest dodawany numer na końcu nazwy, jeśli to konieczne uniknąć zduplikowanych nazw w tej samej przestrzeni nazw.  
  
- Kolorów, rozmiarów i kształtów  
  
- Stereotypów i profili pakietu  
  
- Wartości właściwości, takie jak jest abstrakcyjny  
  
- Połączone elementy robocze  
  
- Liczebność punktów i inne właściwości relacji  
  
- Względne położenie kształtów.  
  
  Następujące funkcje nie zostaną zachowane w niestandardowego narzędzia:  
  
- Kształty proste. Są to kształty, które nie są powiązane z elementami modelu można rysować na niektóre rodzaje diagramów.  
  
- Łącznik routingu. Jeśli ręczne trasowanie łączników routingu będzie nie zostać zachowane podczas służy narzędzie. Położenie niektórych kształtów zagnieżdżonych, takie jak porty, nie są zachowywane względem ich właścicieli.  
  
## <a name="tbxinfo"></a> Jak zdefiniować właściwości niestandardowych narzędzi  
 Informacji przybornika (**.tbxinfo**) plik pozwala określić nazwę przybornika, ikony, etykietki narzędzia, karta i słowo kluczowe dla co najmniej jedno niestandardowe narzędzie pomocy. Nadać mu dowolną nazwę, taką jak **MyTools.tbxinfo**.  
  
 Plik w postaci ogólnego jest następująca:  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<customToolboxItems xmlns="http://schemas.microsoft.com/visualstudio/[version]/ArchitectureTools/CustomToolboxItems">  
  <customToolboxItem fileName="MyObserverTool.classdiagram">  
    <displayName>  
       <value>Observer Pattern</value>  
    </displayName>  
    <tabName>  
       <value>UML Class Diagram</value>  
    </tabName>  
    <image><bmp fileName="ObserverPatternIcon.bmp"/></image>  
    <f1Keyword>  
      <value>ObserverPatternHelp</value>  
    </f1Keyword>  
    <tooltip>  
       <value>Create a pair of classes</value>  
    </tooltip>  
  </customToolboxItem>  
</customToolboxItems>  
```  
  
 Wartość każdego elementu można:  
  
- Jak pokazano w przykładzie `<bmp fileName="…"/>` ikony przybornika i `<value>string</value>` dla innych elementów.  
  
  \- lub —  
  
- `<resource fileName="Resources.dll"`  
  
   `baseName="Observer.resources" id="Observer.tabname" />`  
  
   W takim przypadku użytkownik poda skompilowanego zestawu, w którym zostały skompilowane wartości ciągu jako zasoby.  
  
  Dodaj `<customToolboxItem>` węzła dla każdego elementu przybornika, aby zdefiniować.  
  
  Węzły w **.tbxinfo** znajdują się w następujący sposób. Ma wartość domyślną dla każdego węzła.  
  
|Nazwa węzła|Definiuje|  
|---------------|-------------|  
|displayName|Nazwa elementu przybornika.|  
|tabName|Karta przybornika, w której element powinien pojawiać się. Można określić nazwę dla tego typu diagramu zwykłej karcie lub odrębną nazwę.|  
|obraz|Lokalizacja, mapy bitowej (**.bmp**) plik, który musi mieć wysokość i szerokość 16 i głębi kolorów 24 bity.|  
|f1Keyword|Słowo kluczowe, która lokalizuje tematu Pomocy.|  
|tooltip|Etykietka narzędzia dla tego narzędzia.|  
  
 Edytuj plik mapy bitowej w programie Visual Studio i równa jego wysokości i szerokości 16 w oknie dialogowym właściwości.  
  
> [!NOTE]
>  W przypadku uruchomienia przy użyciu pliku .tbxinfo po eksperymentowanie z używaniem plików diagramu na ich własnych, może się okazać, że Przybornik zawiera zarówno stare i nowe wersje elementu przybornika. Może to także wystąpić, jeśli nazwa pliku diagramu została wpisana z błędem w pliku .tbxinfo. Jeśli ten problem wystąpi, w menu skrótów w przyborniku wybierz **resetowania przybornika**. Elementy do przybornika niestandardowego znikną. Uruchom ponownie program Visual Studio i pojawi się odpowiednie elementy niestandardowe.  
  
## <a name="Extension"></a> Jak dystrybuować elementów przybornika w rozszerzenia programu Visual Studio  
 Można rozpowszechniać elementów przybornika z innymi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] użytkowników upakowanie je do programu Visual Studio rozszerzenia (VSIX). Można spakować poleceń, profile i inne rozszerzenia, w tym samym pliku VSIX. Aby uzyskać więcej informacji, zobacz [wdrażanie rozszerzeń programu Visual Studio](http://go.microsoft.com/fwlink/?LinkId=160780).  
  
 Zwykły sposób do tworzenia rozszerzenia programu Visual Studio jest użycie szablonu projektu VSIX. Aby to zrobić, należy zainstalować [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)].  
  
#### <a name="to-add-a-toolbox-item-to-a-visual-studio-extension"></a>Aby dodać element przybornika do rozszerzenia programu Visual Studio  
  
1. [Tworzenie i testowanie co najmniej jedno narzędzie niestandardowe](#DefineTool).  
  
2. [Utwórz plik .tbxinfo](#tbxinfo) odwołujący się narzędzia.  
  
3. Otwórz istniejący projekt rozszerzenia Visual Studio.  
  
     \- lub —  
  
     Zdefiniuj nowy projekt rozszerzenia Visual Studio.  
  
    1. Na **pliku** menu, wybierz **New**, **projektu**.  
  
    2. W **nowy projekt** dialogowego **zainstalowane szablony**, wybierz **Visual C#**, **rozszerzalności**, **VSIX Projekt**.  
  
4. Dodaj do definicji przybornika do projektu. Obejmują **.tbxinfo** plików, pliki diagramu, pliki map bitowych i pliki zasobów i upewnij się, że są one uwzględnione w VSIX.  
  
    - W Eksploratorze rozwiązań w menu skrótów projektu VSIX wybierz **Dodaj**, **istniejący element**. W oknie dialogowym Ustaw **obiekty typu: Wszystkie pliki**. Znajdź pliki, zaznacz je, a następnie wybierz **Dodaj**.  
  
        > [!NOTE]
        >  W tym projekcie nie można otworzyć plików diagramu w edytorze modeli.  
  
5. Ustaw następujące właściwości wszystkich plików, które zostały dodane. W tym samym czasie można ustawiać ich właściwości, wybierając je w Eksploratorze rozwiązań. Należy zachować ostrożność nie należy zmieniać właściwości inne pliki w projekcie.  
  
     **Kopiuj do katalogu wyjściowego** = **zawsze Kopiuj**  
  
     **Akcja kompilacji** = **zawartości**  
  
     **Uwzględnione w VSIX** = **true**  
  
6. Otwórz **source.extension.vsixmanifest**. Zostanie otwarty w edytorze manifesty rozszerzenia.  
  
7. W obszarze **metadanych**, Dodaj opis narzędzi niestandardowych.  
  
     W obszarze **zasoby**, wybierz **New** , a następnie ustaw pola w oknie dialogowym w następujący sposób:  
  
    - **Typ** = **niestandardowe rozszerzenia typu**  
  
    - Typ = `Microsoft.VisualStudio.ArchitectureTools.CustomToolboxItems`  
  
        > [!NOTE]
        >  Nie jest jedną z opcji na liście rozwijanej. Musisz wprowadzić go za pomocą klawiatury.  
  
    - **Źródło** = **plików w systemie plików**.  
  
    - **Ścieżka** = swoje **.tbxinfo** pliku, na przykład **MyTools.tbxinfo**  
  
8. Skompiluj projekt.  
  
9. **Aby sprawdzić, czy rozszerzenie działa**, naciśnij klawisz F5. Uruchamia doświadczalne wystąpienie programu Visual Studio.  
  
     W doświadczalnym wystąpieniu Utwórz lub Otwórz diagram UML odpowiedniego typu. Sprawdź, czy do nowego narzędzia jest wyświetlana w przyborniku i że tworzy ono elementy poprawnie.  
  
10. **Aby uzyskać plik VSIX do wdrożenia:** W Eksploratorze Windows otwórz folder **.\bin\Debug** lub **.\bin\Release** można znaleźć **.vsix** pliku. Jest to [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] rozszerzenie pliku. Go może być zainstalowana na danym komputerze i również wysyłane do innych użytkowników programu Visual Studio.  
  
#### <a name="to-install-custom-tools-from-a-visual-studio-extension"></a>Aby zainstalować narzędzia niestandardowe z rozszerzenia programu Visual Studio  
  
1. Otwórz `.vsix` plik w Eksploratorze Windows lub w programie Visual Studio.  
  
2. Wybierz **zainstalować** w zostanie wyświetlone okno dialogowe.  
  
3. Aby odinstalować lub tymczasowo wyłączyć rozszerzenie, otwórz **rozszerzenia i aktualizacje** z **narzędzia** menu.  
  
## <a name="localization"></a>Lokalizacja  
 Istnieje możliwość rozszerzenia, które zainstalowanego na innym komputerze, spowoduje wyświetlenie nazwy narzędzia i etykietki narzędzi w języku komputera docelowego.  
  
#### <a name="to-provide-versions-of-the-tool-in-more-than-one-language"></a>Aby zapewnić wersje narzędzia w więcej niż jednym języku  
  
1. Utwórz projekt rozszerzenia Visual Studio, który zawiera co najmniej jedno narzędzie niestandardowe.  
  
    W **.tbxinfo** pliku, użyj metody plików zasobów do definiowania narzędzia `displayName`, przybornika `tabName`i etykietkę narzędzia. Tworzenie pliku zasobów, w której są zdefiniowane następujące ciągi, wkompilować ją w zestaw i odwołują się do niego z pliku tbxinfo.  
  
2. Tworzenie dodatkowych zestawów, które zawierają pliki zasobów ciągów w innych językach.  
  
3. Umieść każdego dodatkowego zestawu w folderze, w której nazwa to kodu kultury dla języka. Na przykład umieścić Francuska wersja językowa zestawu wewnątrz folderu, który nosi nazwę **fr**.  
  
4. Należy używać kodu kultury neutralnej, zazwyczaj dwóch liter, określonej kultury takiej jak `fr-CA`. Aby uzyskać więcej informacji na temat kodów kultury, zobacz [metoda CultureInfo.GetCultures](http://go.microsoft.com/fwlink/?LinkId=160782), który zawiera pełną listę kodów kultur.  
  
5. Tworzenie rozszerzenia programu Visual Studio i rozpowszechnić je.  
  
6. Jeśli rozszerzenie jest zainstalowane na innym komputerze, wersję pliku zasobów dla kultury lokalnego użytkownika zostaną załadowane automatycznie. Jeśli nie podano wersji dla kultury użytkownika, będą używane domyślne zasoby.  
  
   Ta metoda nie umożliwia instalowanie różnych wersji diagram prototypu. Nazwy elementów oraz łączniki będą takie same, w każdej instalacji.  
  
## <a name="other-toolbox-operations"></a>Inne operacje przybornika  
 Zazwyczaj w [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], przybornika można spersonalizować, zmiana nazwy narzędzia, przeniesienie ich do karty innej przybornika i ich usuwania. Jednak te zmiany nie są zachowywane dla narzędzi do modelowania niestandardowe utworzone przy użyciu procedur, które są opisane w tym temacie. Po ponownym uruchomieniu [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], niestandardowe narzędzia pojawi się wraz z ich zdefiniowane nazwy i lokalizacje przybornika.  
  
 Ponadto znikają Twojego niestandardowego narzędzia w sytuacji, gdy wykonujesz **resetowania przybornika** polecenia. Jednak ich pojawi się ponownie po ponownym uruchomieniu [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie modeli i diagramów UML](../modeling/extend-uml-models-and-diagrams.md)   
 [Definiowanie profilu w celu rozszerzenia UML](../modeling/define-a-profile-to-extend-uml.md)   
 [Definiowanie polecenia menu na diagramie modelowania](../modeling/define-a-menu-command-on-a-modeling-diagram.md)   
 [Definiowanie ograniczeń walidacji dla modeli UML](../modeling/define-validation-constraints-for-uml-models.md)
