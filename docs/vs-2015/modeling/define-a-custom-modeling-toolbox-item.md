---
title: Definiowanie niestandardowego elementu przybornika modelowania | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending, customizing the toolbox
ms.assetid: a2463606-1100-40ac-97f3-5ba22ca47b7c
caps.latest.revision: 33
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ac299f18e544ef4f3215707abbdc3d9e8d266de6
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299288"
---
# <a name="define-a-custom-modeling-toolbox-item"></a>Definiowanie niestandardowego elementu przybornika modelowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby ułatwić tworzenie elementu lub grupy elementów zgodnie ze wzorcem, który jest często używany, można dodać nowe narzędzia do przybornika diagramów modelowania w programie Visual Studio. Te elementy przybornika można dystrybuować do innych użytkowników programu Visual Studio.

 Aby sprawdzić, które wersje programu Visual Studio obsługują tę funkcję, zobacz [Obsługa wersji dla narzędzi architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Niestandardowe narzędzie tworzy jeden lub więcej elementów na diagramie. Można na przykład utworzyć niestandardowe narzędzie do tworzenia takich elementów:

- Pakiet połączony z profilem platformy .NET i Klasa z stereotypem platformy .NET.

- Para klas połączonych przez skojarzenie do reprezentowania wzorca obserwatora.

> [!NOTE]
> Tej metody można użyć do tworzenia narzędzi elementów. Oznacza to, że możesz tworzyć narzędzia przeciągane z przybornika na diagram. Nie można tworzyć narzędzi łączników.

## <a name="DefineTool"></a>Definiowanie niestandardowego narzędzia do modelowania

#### <a name="to-define-a-custom-modeling-tool"></a>Aby zdefiniować niestandardowe narzędzie modelowania

1. Utwórz diagram UML zawierający element lub grupę elementów.

    - Te elementy mogą zawierać relacje między nimi i mogą mieć elementy zależne, takie jak porty, atrybuty, operacje lub numery PIN.

2. Zapisz diagram przy użyciu nazwy, która ma zostać nadana nowemu narzędziu. W menu **plik** Użyj polecenie **Zapisz... Tak jak**.

3. Korzystając z Eksploratora Windows, skopiuj dwa pliki diagramu do następującego folderu lub dowolnego podfolderu:

     **Elementy przybornika YourDocuments \Visual Studio\Architecture Tools\Custom**

    - Utwórz ten folder, jeśli jeszcze nie istnieje. Może być konieczne utworzenie zarówno **narzędzi architektury** , jak i **niestandardowych elementów przybornika**.

    - Skopiowanie obu plików diagramu — jeden z nazwą kończącą się ciągiem "... **Diagram**"i drugi o nazwie kończącej się znakiem"... **Diagram. układ**

    - Możesz wprowadzić dowolną liczbę narzędzi niestandardowych. Użyj jednego diagramu dla każdego narzędzia.

4. Obowiązkowe Utwórz plik **. tbxinfo** , zgodnie z opisem w artykule [jak zdefiniować właściwości narzędzi niestandardowych](#tbxinfo)i dodać go do tego samego katalogu. Pozwala to definiować ikonę przybornika, etykietkę narzędzia i tak dalej.

    - Pojedynczy plik **tbxinfo** może służyć do definiowania kilku narzędzi. Może odwoływać się do plików diagramu, które znajdują się w podfolderach.

5. Uruchom ponownie program Visual Studio. Dodatkowe narzędzie pojawi się w przyborniku dla odpowiedniego typu diagramu.

### <a name="what-the-custom-tool-will-replicate"></a>Co zostanie zreplikowane w narzędziu niestandardowym
 Narzędzie niestandardowe będzie replikować większość funkcji diagramu źródłowego:

- Nazwisko. Gdy element jest tworzony z przybornika, w razie potrzeby jest dodawana liczba do końca nazwy, aby uniknąć zduplikowanych nazw w tej samej przestrzeni nazw.

- Kolory, rozmiary i kształty

- Stereotypy i profile pakietów

- Wartości właściwości, takie jak są abstrakcyjne

- Połączone elementy robocze

- Mnożenia i inne właściwości relacji

- Względne położenie kształtów.

  Następujące funkcje nie zostaną zachowane w niestandardowym narzędziu:

- Kształty proste. Są to kształty, które nie są powiązane z elementami modelu, które można rysować na niektórych typach diagramów.

- Routing łączników. Jeśli łączniki są kierowane ręcznie, routing nie zostanie zachowany, gdy używane jest narzędzie. Pozycje niektórych zagnieżdżonych kształtów, takich jak porty, nie są zachowywane względem właścicieli.

## <a name="tbxinfo"></a>Jak definiować właściwości narzędzi niestandardowych
 Plik informacji o przyborniku ( **. tbxinfo**) umożliwia określenie nazwy przybornika, ikony, etykietki narzędzia, karty i słowa kluczowego pomocy dla co najmniej jednego narzędzia niestandardowego. Nadaj mu dowolną nazwę, taką jak **Narzędzia. tbxinfo**.

 Ogólna postać pliku jest następująca:

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

 Każdy element może mieć jedną z wartości:

- Jak pokazano w przykładzie, `<bmp fileName="…"/>` dla ikony przybornika i `<value>string</value>` dla innych elementów.

  \- lub —

- `<resource fileName="Resources.dll"`

   `baseName="Observer.resources" id="Observer.tabname" />`

   W takim przypadku należy dostarczyć skompilowany zestaw, w którym wartości ciągu zostały skompilowane jako zasoby.

  Dodaj węzeł `<customToolboxItem>` dla każdego elementu przybornika, który ma zostać zdefiniowany.

  Węzły w pliku **. tbxinfo** są następujące. Dla każdego węzła istnieje wartość domyślna.

|Nazwa węzła|definiuje|
|---------------|-------------|
|displayName|Nazwa elementu przybornika.|
|tabName|Karta przybornika, w której element powinien zostać wyświetlony. Możesz określić nazwę zwykłej karty dla tego typu diagramu lub oddzielną nazwę.|
|image|Lokalizacja pliku mapy bitowej ( **. bmp**), która musi mieć wysokość i szerokość 16 oraz głębi koloru 24 bity.|
|f1Keyword|Słowo kluczowe, które lokalizuje temat pomocy.|
|wyowietlon|Etykieta narzędzia dla tego narzędzia.|

 Plik mapy bitowej można edytować w programie Visual Studio i ustawić jego wysokość i szerokość na 16 w okno Właściwości.

> [!NOTE]
> Jeśli zaczniesz korzystać z pliku. tbxinfo po eksperymentie przy użyciu plików diagramu, może się okazać, że Przybornik zawiera zarówno starą, jak i nową wersję elementu przybornika. Może to również wystąpić, jeśli nazwa pliku diagramu została wpisana w pliku tbxinfo. W takim przypadku w menu skrótów przybornika wybierz pozycję **Zresetuj Przybornik**. Niestandardowe elementy przybornika znikną. Uruchom ponownie program Visual Studio, a zostaną wyświetlone poprawne elementy niestandardowe.

## <a name="Extension"></a>Jak dystrybuować elementy przybornika w rozszerzeniu programu Visual Studio
 Elementy przybornika można dystrybuować do innych [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] użytkowników, pakując je do rozszerzenia programu Visual Studio (VSIX). Można spakować polecenia, profile i inne rozszerzenia do tego samego pliku VSIX. Aby uzyskać więcej informacji, zobacz [Wdrażanie rozszerzeń programu Visual Studio](https://go.microsoft.com/fwlink/?LinkId=160780).

 Typowym sposobem tworzenia rozszerzenia programu Visual Studio jest użycie szablonu projektu VSIX. Aby to zrobić, musisz mieć zainstalowany [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)].

#### <a name="to-add-a-toolbox-item-to-a-visual-studio-extension"></a>Aby dodać element przybornika do rozszerzenia programu Visual Studio

1. [Tworzenie i testowanie jednego lub kilku narzędzi niestandardowych](#DefineTool).

2. [Utwórz plik. tbxinfo](#tbxinfo) , który odwołuje się do narzędzi.

3. Otwórz istniejący projekt rozszerzenia programu Visual Studio.

     \- lub —

     Zdefiniuj nowy projekt rozszerzenia programu Visual Studio.

    1. W menu **plik** wybierz polecenie **Nowy**, **projekt**.

    2. W oknie dialogowym **Nowy projekt** w obszarze **zainstalowane szablony**wybierz pozycję **Wizualizacja C#** , **rozszerzalność**, **Projekt VSIX**.

4. Dodaj definicje przybornika do projektu. Dołącz plik **. tbxinfo** , pliki diagramu, pliki map bitowych i pliki zasobów oraz upewnij się, że są one uwzględnione w VSIX.

    - W Eksplorator rozwiązań, w menu skrótów projektu VSIX, wybierz **Dodaj**, **istniejący element**. W oknie dialogowym Ustaw **obiekty typu: wszystkie pliki**. Znajdź pliki, zaznacz je wszystkie, a następnie wybierz pozycję **Dodaj**.

        > [!NOTE]
        > W tym projekcie nie można otworzyć plików diagramu w edytorze modelu.

5. Ustaw następujące właściwości wszystkich plików, które zostały właśnie dodane. Można ustawić właściwości w tym samym czasie, wybierając je wszystkie w Eksplorator rozwiązań. Należy zachować ostrożność, aby nie zmieniać właściwości innych plików w projekcie.

     **Kopiuj do katalogu wyjściowego** = **Kopiuj zawsze**

     **Akcja kompilacji** = **zawartość**

     **Uwzględnij w VSIX** = **true**

6. Open **source. Extension. vsixmanifest**. Zostanie on otwarty w edytorze manifestu rozszerzenia.

7. W obszarze **metadane**Dodaj opis narzędzi niestandardowych.

     W obszarze **zasoby**wybierz pozycję **Nowy** , a następnie ustaw pola w oknie dialogowym w następujący sposób:

    - **Typ** **niestandardowego typu rozszerzenia** = 

    - Typ = `Microsoft.VisualStudio.ArchitectureTools.CustomToolboxItems`

        > [!NOTE]
        > Nie jest to jedna z opcji na liście rozwijanej. Musisz go wprowadzić przy użyciu klawiatury.

    - Plik = **źródłowego** **w systemie plików**.

    - **Path** = plik **. tbxinfo** , na przykład **Narzędzia. tbxinfo**

8. Skompiluj projekt.

9. **Aby sprawdzić, czy rozszerzenie działa**, naciśnij klawisz F5. Zostanie uruchomione eksperymentalne wystąpienie programu Visual Studio.

     W eksperymentalnym wystąpieniu Utwórz lub Otwórz diagram UML odpowiedniego typu. Sprawdź, czy nowe narzędzie jest wyświetlane w przyborniku i czy prawidłowo tworzy elementy.

10. **Aby uzyskać plik VSIX dla wdrożenia:** W Eksploratorze Windows otwórz folder **.\bin\debug** lub **.\bin\Release** , aby znaleźć plik **. vsix** . To jest plik rozszerzenia [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]. Można go zainstalować na komputerze, a także wysyłać do innych użytkowników programu Visual Studio.

#### <a name="to-install-custom-tools-from-a-visual-studio-extension"></a>Aby zainstalować narzędzia niestandardowe z rozszerzenia programu Visual Studio

1. Otwórz plik `.vsix` w Eksploratorze Windows lub w programie Visual Studio.

2. W wyświetlonym oknie dialogowym wybierz pozycję **Zainstaluj** .

3. Aby odinstalować lub tymczasowo wyłączyć rozszerzenie, Otwórz **rozszerzenia i aktualizacje** z menu **Narzędzia** .

## <a name="localization"></a>Lokalizacja
 Możesz wprowadzić rozszerzenie, które po zainstalowaniu na innym komputerze spowoduje wyświetlenie nazw narzędzi i etykietek narzędzi w języku komputera docelowego.

#### <a name="to-provide-versions-of-the-tool-in-more-than-one-language"></a>Aby udostępnić wersje narzędzia w więcej niż jednym języku

1. Utwórz projekt rozszerzenia programu Visual Studio, który zawiera co najmniej jeden niestandardowy narzędzi.

    W pliku **. tbxinfo** Użyj metody pliku zasobów, aby zdefiniować `displayName`narzędzia, Przybornik `tabName`i etykietkę narzędzia. Utwórz plik zasobów, w którym są zdefiniowane te ciągi, skompiluj go w zestawie i odwołaj się do niego z pliku tbxinfo.

2. Utwórz dodatkowe zestawy zawierające pliki zasobów z ciągami w innych językach.

3. Umieść każdy dodatkowy zestaw w folderze, którego nazwa jest kodem kultury dla danego języka. Na przykład Umieść wersję francuską zestawu w folderze o nazwie **fr**.

4. Należy używać neutralnego kodu kulturowego, zwykle dwóch liter, a nie określonej kultury, takiej jak `fr-CA`. Aby uzyskać więcej informacji na temat kodów kultur, zobacz [Metoda CultureInfo. GetCultures](https://go.microsoft.com/fwlink/?LinkId=160782), która zawiera kompletną listę kodów kultur.

5. Kompiluj rozszerzenie programu Visual Studio i Rozpowszechnij go.

6. Gdy rozszerzenie zostanie zainstalowane na innym komputerze, zostanie automatycznie załadowana wersja pliku zasobów dla kultury lokalnej użytkownika. Jeśli nie podano wersji kultury użytkownika, zostaną użyte domyślne zasoby.

   Nie można użyć tej metody, aby zainstalować różne wersje diagramu prototypowego. Nazwy elementów i łączników będą takie same w każdej instalacji.

## <a name="other-toolbox-operations"></a>Inne operacje przybornika
 Zwykle w [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]można personalizować Przybornik, zmieniając nazwy narzędzi, przenosząc je do różnych kart przybornika i usuwając je. Jednak te zmiany nie są utrwalane w przypadku niestandardowych narzędzi modelowania utworzonych za pomocą procedur opisanych w tym temacie. Po ponownym uruchomieniu [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]narzędzia niestandardowe pojawią się ponownie wraz ze zdefiniowanymi nazwami i lokalizacjami przybornika.

 Ponadto narzędzia niestandardowe znikną po wykonaniu polecenia **Zresetuj Przybornik** . Jednak zostaną one wyświetlone ponownie po ponownym uruchomieniu [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].

## <a name="see-also"></a>Zobacz też
 [Rozszerzając modele UML i diagramy](../modeling/extend-uml-models-and-diagrams.md) [Definiuj profil do rozszerania UML](../modeling/define-a-profile-to-extend-uml.md) [Zdefiniuj polecenie menu na diagramie modelowania](../modeling/define-a-menu-command-on-a-modeling-diagram.md) [Definiowanie ograniczeń walidacji dla modeli UML](../modeling/define-validation-constraints-for-uml-models.md)
