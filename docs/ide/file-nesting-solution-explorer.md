---
title: Reguły zagnieżdżania plików dla Eksplorator rozwiązań
description: Dowiedz się więcej na temat reguł zagnieżdżania plików Eksplorator rozwiązań, ustawień wstępnych i dostosowywania.
ms.custom: SEO-VS-2020
ms.date: 05/25/2018
ms.topic: conceptual
helpviewer_keywords:
- file nesting
- Solution Explorer, file nesting
author: angelosp
ms.author: angelpe
manager: jillfra
ms.openlocfilehash: 5425c255e85a2785383f1e8e718340fc2049e0c4
ms.sourcegitcommit: 66cda27b63c9b55782b1db223a6dbda9f8cabe13
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2020
ms.locfileid: "95006695"
---
# <a name="file-nesting-in-solution-explorer"></a>Zagnieżdżanie plików w Eksploratorze rozwiązań

**Eksplorator rozwiązań** zagnieżdża powiązane pliki, aby ułatwić ich organizowanie i ułatwić ich lokalizowanie. Na przykład jeśli dodasz formularz Windows Forms do projektu, plik kodu dla formularza zostanie zagnieżdżony poniżej formularza w **Eksplorator rozwiązań**. W projektach ASP.NET Core zagnieżdżenia plików można wykonać krokowo. Można wybrać między ustawieniami zagnieżdżenia plików **wyłączonymi**, **domyślnymi** i **sieci Web**. Można również [dostosować sposób zagnieżdżania plików](#customize-file-nesting) lub tworzyć ustawienia specyficzne dla konkretnego [rozwiązania i projektu](#create-project-specific-settings).

> [!NOTE]
> Ta funkcja jest obecnie obsługiwana tylko w projektach ASP.NET Core.

## <a name="file-nesting-options"></a>Opcje zagnieżdżania plików

![Przycisk służący do włączania/wyłączania zagnieżdżania plików](media/filenesting_onoff.png)

Dostępne opcje zagnieżdżania plików są następujące:

* **Wyłączone**: Ta opcja zapewnia płaską listę plików bez zagnieżdżenia.

* **Wartość domyślna**: Ta opcja zapewnia domyślne zachowanie zagnieżdżania plików w **Eksplorator rozwiązań**. Jeśli nie istnieją żadne ustawienia dla danego typu projektu, nie są zagnieżdżane żadne pliki w projekcie. Jeśli istnieją ustawienia, na przykład dla projektu sieci Web, jest stosowane zagnieżdżanie.

* **Sieć Web**: Ta opcja stosuje zachowanie zagnieżdżania plików **sieci Web** do wszystkich projektów w bieżącym rozwiązaniu. Ma wiele reguł i zachęca Cię do wyewidencjonowania go i poinformowania nas o tym, co myślisz. Poniższy zrzut ekranu przedstawia zaledwie kilka przykładów zachowań zagnieżdżania plików, które można uzyskać przy użyciu tej opcji:

   ![Zagnieżdżanie plików w Eksploratorze rozwiązań](media/filenesting.png)

## <a name="customize-file-nesting"></a>Dostosowywanie zagnieżdżania plików

Jeśli nie chcesz, aby to zrobić, możesz utworzyć własne, niestandardowe ustawienia zagnieżdżania plików, które poinstruują **Eksplorator rozwiązań** jak zagnieżdżać pliki. Możesz dodać dowolną liczbę niestandardowych ustawień zagnieżdżania plików i można przełączać się między nimi. Aby utworzyć nowe ustawienie niestandardowe, możesz rozpocząć od pustego pliku lub użyć ustawień **sieci Web** jako punktu początkowego:

![Dodawanie niestandardowych reguł zagnieżdżania plików](media/filenesting_addcustom.png)

Zalecamy korzystanie z ustawień **sieci Web** jako punktu początkowego, ponieważ ułatwia to pracę z coś, co już działa. Jeśli używasz ustawień **sieci Web** jako punktu początkowego, *.filenesting.js* pliku wygląda podobnie do następującego pliku:

![Użyj istniejących reguł zagnieżdżania plików jako podstawy dla ustawień niestandardowych](media/filenesting_editcustom.png)

Skupmy się na węźle **dependentFileProviders** i jego węzłach podrzędnych. Każdy węzeł podrzędny jest typem reguły, która może być używana przez program Visual Studio do zagnieżdżania plików. Na przykład ma taką **samą nazwę pliku, ale inne rozszerzenie** jest jednym typem reguły. Dostępne są następujące reguły:

* **extensionToExtension**: Użyj tego typu reguły, aby zagnieździć *file.js* w *pliku. TS*

* **fileSuffixToExtension**: Użyj tego typu reguły, aby zagnieździć *file-vsdoc.js* w *file.js*

* **addedExtension**: Użyj tego typu reguły, aby zagnieździć *file.html. css* w obszarze *file.html*

* **pathSegment**: Użyj tego typu reguły, aby zagnieździć *jquery.min.js* w *jquery.js*

* **allExtensions**: Użyj tego typu reguły, aby zagnieździć *plik.* * w obszarze *file.js*

* **fileToFile**: Użyj tego typu reguły, aby zagnieździć *bower.jsw* obszarze *. bowerrc*

### <a name="the-extensiontoextension-provider"></a>Dostawca extensionToExtension

Ten dostawca umożliwia definiowanie reguł zagnieżdżania plików przy użyciu określonych rozszerzeń plików. Rozpatrzmy następujący przykład:

![extentionToExtension przykładowe reguły](media/filenesting_extensiontoextension.png) ![Przykładowy efekt extentionToExtension](media/filenesting_extensiontoextension_effect.png)

* *cart.js* jest zagnieżdżona w obszarze *koszyka. TS* z powodu pierwszej reguły **extensionToExtension**

* *cart.js* nie jest zagnieżdżona w obszarze *Cart. TSX* , ponieważ **. TS** znajduje się przed **. TSX** w regułach, a może istnieć tylko jeden element nadrzędny

* *Light. css* jest zagnieżdżony pod właściwością *Light. Sass* ze względu na drugą regułę **extensionToExtension**

* *home.html* jest zagnieżdżona w obszarze *Home.MD* z powodu trzeciej reguły **extensionToExtension**

### <a name="the-filesuffixtoextension-provider"></a>Dostawca fileSuffixToExtension

Ten dostawca działa podobnie jak w przypadku dostawcy **extensionToExtension** . jedyną różnicą jest to, że reguła przegląda sufiks pliku, a nie tylko rozszerzenie. Rozpatrzmy następujący przykład:

![fileSuffixToExtension przykładowe reguły](media/filenesting_filesuffixtoextension.png) ![Przykładowy efekt fileSuffixToExtension](media/filenesting_filesuffixtoextension_effect.png)

* *portal-vsdoc.js* jest zagnieżdżona w *portal.js* ze względu na regułę **fileSuffixToExtension**

* Każdy inny aspekt reguły działa tak samo jak **extensionToExtension**

### <a name="the-addedextension-provider"></a>Dostawca addedExtension

Ten dostawca zagnieżdża pliki z dodatkowym rozszerzeniem w pliku bez dodatkowego rozszerzenia. Dodatkowe rozszerzenie może pojawić się tylko na końcu pełnej nazwy pliku.

Rozpatrzmy następujący przykład:

![addedExtension przykładowe reguły](media/filenesting_addedextension.png) ![Przykładowy efekt addedExtension](media/filenesting_addedextension_effect.png)

* *file.html. css* jest zagnieżdżony w *file.html* z powodu reguły **addedExtension**

> [!NOTE]
> Nie określono żadnych rozszerzeń plików dla `addedExtension` reguły; automatycznie stosuje się do wszystkich rozszerzeń plików. Oznacza to, że każdy plik o takiej samej nazwie i rozszerzeniu, co inny plik oraz dodatkowe rozszerzenie na końcu, jest zagnieżdżony w innym pliku. Nie można ograniczyć efektu tego dostawcy tylko do określonych rozszerzeń plików.

### <a name="the-pathsegment-provider"></a>Dostawca pathSegment

Ten dostawca zagnieżdża pliki z dodatkowym rozszerzeniem w pliku bez dodatkowego rozszerzenia. Dodatkowe rozszerzenie może pojawić się tylko w środku pełnej nazwy pliku.

Rozpatrzmy następujący przykład:

![pathSegment przykładowe reguły](media/filenesting_pathsegment.png) ![Przykładowy efekt pathSegment](media/filenesting_pathsegment_effect.png)

* *jquery.min.js* jest zagnieżdżona w *jquery.js* ze względu na regułę **pathSegment**

> [!NOTE]
> - Jeśli nie określisz żadnych określonych rozszerzeń plików dla `pathSegment` reguły, dotyczy to wszystkich rozszerzeń plików. Oznacza to, że każdy plik o takiej samej nazwie i rozszerzeniu, co inny plik oraz dodatkowe rozszerzenie w środku, jest zagnieżdżony w innym pliku.
> - Można ograniczyć efekt `pathSegment` reguły do określonych rozszerzeń plików, określając je w następujący sposób:
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

### <a name="the-allextensions-provider"></a>Dostawca allExtensions

Ten dostawca umożliwia zdefiniowanie reguł zagnieżdżania plików dla plików z dowolnym rozszerzeniem, ale z tą samą nazwą pliku podstawowego. Rozpatrzmy następujący przykład:

![allExtensions przykładowe reguły](media/filenesting_allextensions.png) ![Przykładowy efekt allExtensions](media/filenesting_allextensions_effect.png)

* *Template.cs* i *template.doc* są zagnieżdżone w obszarze *Template.tt* ze względu na regułę **allExtensions** .

### <a name="the-filetofile-provider"></a>Dostawca fileToFile

Ten dostawca umożliwia zdefiniowanie reguł zagnieżdżania plików na podstawie całych nazw plików. Rozpatrzmy następujący przykład:

![fileToFile przykładowe reguły](media/filenesting_filetofile.png) ![Przykładowy efekt fileToFile](media/filenesting_filetofile_effect.png)

* *. bowerrc* jest zagnieżdżona w obszarze *bower.jsna* skutek reguły **fileToFile**

### <a name="rule-order"></a>Kolejność reguł

Kolejność jest ważna w każdej części pliku ustawień niestandardowych. Można zmienić kolejność, w której reguły są wykonywane, przenosząc je w górę lub w dół w węźle **dependentFileProvider** . Na przykład, jeśli masz jedną regułę, która wprowadza **file.js** elementu nadrzędnego **pliku. TS** i inną regułę, która tworzy **plik. kawy** nadrzędny **pliku. TS**, kolejność, w jakiej są wyświetlane w pliku, określa zachowanie zagnieżdżenia, gdy wszystkie trzy pliki są obecne. Ponieważ **plik. TS** może mieć tylko jeden element nadrzędny, niezależnie od reguły jest przeprowadzana pierwsza usługa WINS.

Kolejność jest również ważna dla samych sekcji reguł, a nie tylko dla plików znajdujących się w sekcji. Po dopasowaniu pary plików z regułą zagnieżdżania plików inne reguły w pliku są ignorowane, a następna para plików jest przetwarzana.

### <a name="file-nesting-button"></a>Przycisk zagnieżdżania plików

Można zarządzać wszystkimi ustawieniami, w tym własnymi ustawieniami niestandardowymi, za pomocą tego samego przycisku w **Eksplorator rozwiązań**:

![Aktywuj niestandardowe reguły zagnieżdżania plików](media/filenesting_activatecustom.png)

## <a name="create-project-specific-settings"></a>Tworzenie ustawień specyficznych dla projektu

Ustawienia specyficzne dla rozwiązania i projektu można utworzyć za pomocą menu rozwijanego prawym przyciskiem myszy (menu kontekstowe) każdego rozwiązania i projektu:

![Rozwiązania i reguły zagnieżdżania specyficzne dla projektu](media/filenesting_solutionprojectspecific.png)

Ustawienia specyficzne dla rozwiązania i projektu są łączone z aktywnymi ustawieniami programu Visual Studio. Na przykład może istnieć pusty plik ustawień specyficznych dla projektu, ale **Eksplorator rozwiązań** nadal zagnieżdża pliki. Zachowanie zagnieżdżania pochodzi z ustawień specyficznych dla rozwiązania lub ustawień programu Visual Studio. Pierwszeństwo scalania ustawień zagnieżdżania plików: Visual Studio > rozwiązanie > Project.

Można poinformować program Visual Studio, aby ignorował ustawienia specyficzne dla rozwiązania i projektu, nawet jeśli pliki znajdują się na dysku, włączając opcję **Ignoruj ustawienia rozwiązania i projektu** w obszarze **Narzędzia**  >  **Opcje**  >  **ASP.NET Core**  >  **zagnieżdżanie plików**.

Można to zrobić odwrotnie i powiadom program Visual Studio, aby używał *tylko* określonych rozwiązań lub ustawień specyficznych dla projektu, ustawiając dla węzła **głównego** **wartość true**. Program Visual Studio przestaje scalać pliki na tym poziomie i nie łączy go z plikami w górę hierarchii.

Ustawienia specyficzne dla rozwiązania i projektu można sprawdzić w kontroli źródła, a cały zespół, który działa w bazie kodu, może je udostępnić.

## <a name="disable-file-nesting-rules-for-a-project"></a>Wyłącz reguły zagnieżdżania plików dla projektu

Istniejące globalne reguły zagnieżdżania plików można wyłączyć dla konkretnych rozwiązań lub projektów za pomocą akcji **usuwania** dla dostawcy zamiast polecenia **Dodaj**. Na przykład jeśli dodasz następujący kod ustawień do projektu, wszystkie reguły **pathSegment** , które mogą istnieć globalnie dla tego konkretnego projektu, są wyłączone:

```json
"dependentFileProviders": {
  "remove": {
    "pathSegment": {}
  }
}
```

## <a name="see-also"></a>Zobacz także

- [Personalizowanie środowiska IDE](../ide/personalizing-the-visual-studio-ide.md)
- [Rozwiązania i projekty w programie Visual Studio](solutions-and-projects-in-visual-studio.md)
