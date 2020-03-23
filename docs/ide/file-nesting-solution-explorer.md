---
title: Reguły zagnieżdżania plików dla Eksploratora rozwiązań
ms.date: 05/25/2018
ms.topic: conceptual
helpviewer_keywords:
- file nesting
- Solution Explorer, file nesting
author: angelosp
ms.author: angelpe
manager: jillfra
ms.openlocfilehash: a36ca2535785f72756ad66a69c2ebe4d7d5a373b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "67587024"
---
# <a name="file-nesting-in-solution-explorer"></a>Zagnieżdżanie plików w Eksploratorze rozwiązań

**Eksplorator rozwiązań** zagnieżdża powiązane pliki, aby ułatwić ich organizację i ułatwić ich lokalizowanie. Na przykład po dodaniu formularza Formularze systemu Windows do projektu plik kodu formularza jest zagnieżdżony poniżej formularza w **Eksploratorze rozwiązań**. W projektach ASP.NET Core zagnieżdżanie plików można zrobić o krok dalej. Można wybrać między ustawieniami predefiniowania zagnieżdżania plików **Wyłączone,** **Domyślne**i **Sieć Web**. Można również [dostosować sposób zagnieżdżania plików](#customize-file-nesting) lub utworzyć ustawienia specyficzne dla rozwiązania i specyficzne dla [projektu](#create-project-specific-settings).

> [!NOTE]
> Funkcja jest obecnie obsługiwana tylko dla projektów ASP.NET Core.

## <a name="file-nesting-options"></a>Opcje zagnieżdżania plików

![Przycisk włączania/wyłączania zagnieżdżania plików](media/filenesting_onoff.png)

Dostępne opcje nieprzystosowania zagnieżdżania plików to:

* **Wył.:** Ta opcja umożliwia wyświetlanie płaskiej listy plików bez zagnieżdżania.

* **Domyślnie**: Ta opcja zapewnia domyślne zachowanie zagnieżdżania plików w **Eksploratorze rozwiązań**. Jeśli nie istnieją żadne ustawienia dla danego typu projektu, żadne pliki w projekcie nie są zagnieżdżone. Jeśli istnieją ustawienia, na przykład dla projektu sieci web, zagnieżdżanie jest stosowane.

* **Sieć Web**: Ta opcja stosuje zachowanie zagnieżdżania plików **sieci Web** do wszystkich projektów w bieżącym rozwiązaniu. Ma wiele zasad, a my zachęcamy, aby to sprawdzić i powiedzieć nam, co myślisz. Poniższy zrzut ekranu przedstawia tylko kilka przykładów zachowania zagnieżdżania plików, które można uzyskać za pomocą tej opcji:

   ![Zagnieżdżanie plików w Eksploratorze rozwiązań](media/filenesting.png)

## <a name="customize-file-nesting"></a>Dostosowywanie zagnieżdżania plików

Jeśli nie podoba Ci się to, co ci się nie ma, możesz utworzyć własne, niestandardowe ustawienia zagnieżdżania plików, które poinstruują **Eksploratora rozwiązań,** jak zagnieżdżać pliki. Można dodać dowolną liczbę niestandardowych ustawień zagnieżdżania plików i przełączać się między nimi zgodnie z potrzebami. Aby utworzyć nowe ustawienie niestandardowe, można rozpocząć od pustego pliku lub użyć ustawień **sieci Web** jako punktu wyjścia:

![Dodawanie niestandardowych reguł zagnieżdżania plików](media/filenesting_addcustom.png)

Zaleca się używanie ustawień **sieci Web** jako punktu wyjścia, ponieważ łatwiej jest pracować z czymś, co już działa. Jeśli jako punkt wyjścia są używane ustawienia **sieci Web,** plik *filenesting.json* wygląda podobnie do następującego pliku:

![Używanie istniejących reguł zagnieżdżania plików jako podstawy ustawień niestandardowych](media/filenesting_editcustom.png)

Skupmy się na **węzła zależneFileProviders** i jego węzłów podrzędnych. Każdy węzeł podrzędny jest typem reguły, której program Visual Studio może używać do zagnieżdżania plików. Na przykład **o tej samej nazwy pliku, ale inne rozszerzenie** jest jeden typ reguły. Dostępne zasady to:

* **extensionToExtension**: Użyj tego typu reguły, aby zagnieżdżać *plik.js* w pliku *file.ts*

* **fileSuffixToExtension**: Użyj tego typu reguły, aby zagnieżdżać *plik vsdoc.js* w pliku *file.js*

* **addedExtension**: Użyj tego typu reguły, aby zagnieżdżać *plik.html.css* pod *plikiem file.html*

* **pathSegment**: Użyj tego typu reguły, aby zagnieżdżać *jquery.min.js* pod *jquery.js*

* **allExtensions**: Użyj tego typu reguły, aby zagnieżdżać *plik.* * pod *plikiem file.js*

* **fileToFile**: Użyj tego typu reguły, aby zagnieżdżać *bower.json* pod *.bowerrc*

### <a name="the-extensiontoextension-provider"></a>Dostawca rozszerzeniaToExtension

Ten dostawca umożliwia definiowanie reguł zagnieżdżania plików przy użyciu określonych rozszerzeń plików. Rozważmy następujący przykład:

![reguły przykładowe extentionToExtension](media/filenesting_extensiontoextension.png) ![extentionToExtension przykładowy efekt](media/filenesting_extensiontoextension_effect.png)

* *cart.js* jest zagnieżdżony pod *cart.ts* ze względu na pierwszą regułę **extensionToExtension**

* *cart.js* nie jest zagnieżdżony pod *cart.tsx* ponieważ **.ts** jest przed **.tsx** w zasadach, a może być tylko jeden rodzic

* *light.css* jest zagnieżdżony pod *light.sass* ze względu na drugie **extensionToExtension reguły**

* *home.html* jest zagnieżdżony pod *home.md* z powodu trzeciej reguły **extensionToExtension**

### <a name="the-filesuffixtoextension-provider"></a>Dostawca fileSuffixToExtension

Ten dostawca działa podobnie jak **rozszerzenieDostyczność** dostawcy, z tą tylko różnicą jest to, że reguła patrzy na sufiks pliku, a nie tylko rozszerzenie. Rozważmy następujący przykład:

![fileSuffixToExtension przykładowe reguły](media/filenesting_filesuffixtoextension.png) ![fileSuffixToExtension przykładowy efekt](media/filenesting_filesuffixtoextension_effect.png)

* *portal-vsdoc.js* jest zagnieżdżony w witrynie *portal.js* z powodu reguły **fileSuffixToExtension**

* każdy inny aspekt reguły działa tak samo jak **extensionToExtension**

### <a name="the-addedextension-provider"></a>Dostawca addedExtension

Ten dostawca zagnieżdża pliki z dodatkowym rozszerzeniem pod plikiem bez dodatkowego rozszerzenia. Dodatkowe rozszerzenie może pojawić się tylko na końcu pełnej nazwy pliku.

Rozważmy następujący przykład:

![addedExtension przykładowe reguły](media/filenesting_addedextension.png) ![addedWydaj przykładowy efekt wyeksji](media/filenesting_addedextension_effect.png)

* *plik.html.css* jest zagnieżdżony pod *plikiem file.html* z powodu reguły **addedExtension**

> [!NOTE]
> Nie określasz żadnych rozszerzeń `addedExtension` plików dla reguły; automatycznie stosuje się do wszystkich rozszerzeń plików. Oznacza to, że każdy plik o tej samej nazwie i rozszerzeniu co inny plik oraz dodatkowe rozszerzenie na końcu są zagnieżdżone pod drugim plikiem. Nie można ograniczyć efektu tego dostawcy tylko do określonych rozszerzeń plików.

### <a name="the-pathsegment-provider"></a>ŚcieżkaSegment dostawca

Ten dostawca zagnieżdża pliki z dodatkowym rozszerzeniem pod plikiem bez dodatkowego rozszerzenia. Dodatkowe rozszerzenie może pojawić się tylko na środku pełnej nazwy pliku.

Rozważmy następujący przykład:

![pathSegment przykładowe reguły](media/filenesting_pathsegment.png) ![pathSegment przykładowy efekt](media/filenesting_pathsegment_effect.png)

* *jquery.min.js* jest zagnieżdżony pod *jquery.js* ze względu na **pathSegment reguły**

> [!NOTE]
> - Jeśli nie określisz żadnych konkretnych rozszerzeń plików dla `pathSegment` reguły, dotyczy ona wszystkich rozszerzeń plików. Oznacza to, że każdy plik o tej samej nazwie i rozszerzeniu co inny plik oraz dodatkowe rozszerzenie w środku jest zagnieżdżony pod drugim plikiem.
> - Efekt reguły `pathSegment` można ograniczyć do określonych rozszerzeń plików, określając je w następujący sposób:
>
>    ```json
>    "pathSegment": {
>       "add": {
>         ".*": [
>           ".js",
>           ".css",
>           ".html",
>           ".htm"
>         ]
>       }
>    }
>    ```

### <a name="the-allextensions-provider"></a>Dostawca wszystkichWysokień

Ten dostawca umożliwia definiowanie reguł zagnieżdżania plików dla plików z dowolnym rozszerzeniem, ale o tej samej nazwie pliku podstawowego. Rozważmy następujący przykład:

![allExtensions przykładowe reguły](media/filenesting_allextensions.png) ![allWydaje przykładowy efekt](media/filenesting_allextensions_effect.png)

* *template.cs* i *template.doc* są zagnieżdżone w *obszarze template.tt* ze względu na **regułę allExtensions.**

### <a name="the-filetofile-provider"></a>Dostawca fileToFile

Ten dostawca umożliwia definiowanie reguł zagnieżdżania plików na podstawie całych nazwach plików. Rozważmy następujący przykład:

![reguły przykładowe fileToFile](media/filenesting_filetofile.png) ![Efekt przykładu fileToFile](media/filenesting_filetofile_effect.png)

* *.bowerrc* jest zagnieżdżony pod *bower.json* ze względu na regułę **fileToFile**

### <a name="rule-order"></a>Kolejność reguł

Zamawianie jest ważne w każdej części pliku ustawień niestandardowych. Można zmienić kolejność wykonywania reguł, przenosząc je w górę lub w dół wewnątrz **węzła zależnegoFileProvider.** Na przykład, jeśli masz jedną regułę, która sprawia, że **file.js nadrzędny** **file.ts** i inna reguła, która sprawia, że **file.coffee** jest nadrzędnym **file.ts,** kolejność, w jakiej pojawiają się w pliku, decyduje o zachowaniu zagnieżdżania, gdy wszystkie trzy pliki są obecne. Ponieważ **plik.ts** może mieć tylko jeden element nadrzędny, w zależności od reguły wykonuje pierwsze wygrane.

Zamawianie jest również ważne dla samych sekcji reguł, a nie tylko dla plików w sekcji. Gdy tylko para plików zostanie dopasowana do reguły zagnieżdżania plików, inne reguły znajdujące się w pliku są ignorowane, a następna para plików jest przetwarzana.

### <a name="file-nesting-button"></a>Przycisk zagnieżdżanie plików

Możesz zarządzać wszystkimi ustawieniami, w tym własnymi ustawieniami niestandardowymi, za pomocą tego samego przycisku w **Eksploratorze rozwiązań:**

![Aktywowanie niestandardowych reguł zagnieżdżania plików](media/filenesting_activatecustom.png)

## <a name="create-project-specific-settings"></a>Tworzenie ustawień specyficznych dla projektu

Ustawienia specyficzne dla rozwiązania i specyficzne dla projektu można tworzyć za pomocą menu (menu kontekstowego) każdego rozwiązania i projektu, które umożliwia kliknięcie prawym przyciskiem myszy:

![Reguły zagnieżdżania rozwiązania i specyficzne dla projektu](media/filenesting_solutionprojectspecific.png)

Ustawienia specyficzne dla rozwiązania i specyficzne dla projektu są łączone z aktywnymi ustawieniami programu Visual Studio. Na przykład może być pusty plik ustawień specyficznych dla projektu, ale **Eksplorator rozwiązań** nadal zagnieżdża pliki. Zachowanie zagnieżdżania pochodzi z ustawień specyficznych dla rozwiązania lub ustawień programu Visual Studio. Pierwszeństwo scalania ustawień zagnieżdżania plików ma: Visual Studio > Solution > Project.

Program Visual Studio może zignorować ustawienia specyficzne dla rozwiązania i specyficzne dla projektu, nawet jeśli pliki istnieją na dysku, włączając opcję **Ignoruj ustawienia rozwiązania i projektu** w obszarze**Opcje** >  **narzędzi** > ASP.NET**Zagnieżdżanie plików****podstawowych** > .

Można zrobić odwrotnie i powiedzieć visual studio, aby używał *tylko* ustawień specyficznych dla rozwiązania lub specyficznego dla projektu, ustawiając węzeł **główny** na **true**. Visual Studio zatrzymuje scalanie plików na tym poziomie i nie łączy go z plikami wyżej w hierarchii.

Ustawienia specyficzne dla rozwiązania i specyficzne dla projektu można sprawdzić w kontroli źródła, a cały zespół, który działa w bazie kodu może je udostępnić.

## <a name="disable-file-nesting-rules-for-a-project"></a>Wyłączanie reguł zagnieżdżania plików dla projektu

Istniejące globalne reguły zagnieżdżania plików dla określonych rozwiązań lub projektów można wyłączyć za pomocą akcji **usuwania** dla dostawcy zamiast **dodawania**. Na przykład jeśli dodasz następujący kod ustawień do projektu, wszystkie **reguły pathSegment,** które mogą istnieć globalnie dla tego konkretnego projektu, zostaną wyłączone:

```json
"dependentFileProviders": {
  "remove": {
    "pathSegment": {}
  }
}
```

## <a name="see-also"></a>Zobacz też

- [Personalizowanie ide](../ide/personalizing-the-visual-studio-ide.md)
- [Rozwiązania i projekty w programie Visual Studio](solutions-and-projects-in-visual-studio.md)
