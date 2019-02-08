---
title: Plik reguł zagnieżdżenia Eksploratora rozwiązań
ms.date: 05/25/2018
ms.topic: conceptual
helpviewer_keywords:
- file nesting
- Solution Explorer, file nesting
author: angelosp
ms.author: angelpe
manager: jillfra
ms.openlocfilehash: 58e727c6335dd391abab4f50a110d361a658e00a
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55955989"
---
# <a name="customize-file-nesting-in-solution-explorer"></a>Dostosowywanie zagnieżdżania plików w Eksploratorze rozwiązań

Zagnieżdżanie plików powiązanych z **Eksploratora rozwiązań** nie jest nowy, do czasu, ale teraz masz żadnej kontroli nad tym zagnieżdżenia reguły. Możesz wybrać ustawienia wstępne **wyłączone**, **domyślne** i **sieci Web**, ale można również dostosować zagnieżdżania dokładnie do swoich potrzeb. Możesz nawet utworzyć specyficznych dla rozwiązania i ustawienia specyficzne dla projektu, ale więcej informacji na temat wszystkich później. Najpierw Zajmijmy co można uzyskać, out-of--box.

> [!NOTE]
> Ta funkcja jest obecnie obsługiwana tylko w przypadku projektów ASP.NET Core.

## <a name="file-nesting-options"></a>Opcje zagnieżdżania plików

![Przycisk służący do włączania zagnieżdżania włączenia/wyłączenia plików](media/filenesting_onoff.png)

Dostępne opcje zagnieżdżanie plików bez dostosowania są następujące:

* **Wyłącz**: Ta opcja zapewnia płaską listę plików bez żadnych zagnieżdżania.

* **Domyślne**: Ta opcja powoduje wyświetlenie domyślnego pliku zagnieżdżania zachowanie w **Eksploratora rozwiązań**. Jeśli ustawienia nie istnieje dla typu danego projektu, żadne pliki w projekcie są zagnieżdżone. Jeśli istnieją ustawienia, na przykład dla projektu sieci web, zastosowane zagnieżdżania.

* **Web**: Ta opcja ma zastosowanie **Web** pliku zagnieżdżenia zachowanie dla wszystkich projektów w bieżącym rozwiązaniu. Ma ona wiele reguł, a firma Microsoft zachęca do go wyewidencjonować i powiedz nam, co myślisz. Poniższy zrzut ekranu pokazuje kilka przykładów zachowanie zagnieżdżania plików, której można korzystać z tej opcji:

   ![Plik zagnieżdżania w Eksploratorze rozwiązań](media/filenesting.png)

## <a name="customize-file-nesting"></a>Dostosowywanie zagnieżdżanie plików

Jeśli nie potrzebujesz, co można uzyskać, out-of--box, możesz utworzyć własny, niestandardowy plik ustawienia, które poinstruowanie zagnieżdżania **Eksploratora rozwiązań** jak zagnieżdżanie plików. Można dodać tyle niestandardowego pliku zagnieżdżenia ustawień, ile chcesz, i możesz przełączać się między nimi zgodnie z potrzebami. Aby utworzyć nowe ustawienie niestandardowych, można zacząć od pusty plik, lub możesz użyć **Web** ustawienia jako punkt początkowy:

![Dodawanie niestandardowego pliku reguł zagnieżdżania](media/filenesting_addcustom.png)

Zalecane jest użycie **Web** ustawienia Twoje początkowe punktu, ponieważ jest łatwiej pracować z coś, co już funkcji. Jeśli używasz **Web** ustawienia jako punktu początkowego *. filenesting.json* pliku wygląda podobnie do następującego pliku:

![Użyj istniejącego pliku zagnieżdżania reguły jako podstawy dla ustawień niestandardowych](media/filenesting_editcustom.png)

Skupmy się na węźle **dependentFileProviders** i jego węzłami podrzędnymi. Każdy węzeł podrzędny jest to typ reguły, można użyć programu Visual Studio, aby zagnieździć plików. Na przykład **o takiej samej nazwie pliku, ale inne rozszerzenie** jest jeden typ reguły. Reguły dostępne są następujące:

* **extensionToExtension**: Użyj tego typu reguł, aby zagnieździć *file.js* w obszarze *file.ts*

* **fileSuffixToExtension**: Użyj tego typu reguł, aby zagnieździć *vsdoc.js pliku* w obszarze *file.js*

* **addedExtension**: Użyj tego typu reguł, aby zagnieździć *file.html.css* w obszarze *file.html*

* **pathSegment**: Użyj tego typu reguł, aby zagnieździć *jquery.min.js* w obszarze *jquery.js*

* **allExtensions**: Użyj tego typu reguł, aby zagnieździć *pliku.* * w obszarze *file.js*

* **fileToFile**: Użyj tego typu reguł, aby zagnieździć *bower.json* w obszarze *.bowerrc*

### <a name="the-extensiontoextension-provider"></a>Dostawca extensionToExtension

Ten dostawca umożliwia definiowanie reguł zagnieżdżania plików przy użyciu określonych rozszerzeń plików. Rozważmy następujący przykład:

![extentionToExtension przykładowych reguł](media/filenesting_extensiontoextension.png) ![efekt przykład extentionToExtension](media/filenesting_extensiontoextension_effect.png)

* *Cart.js* jest zagnieżdżony w *cart.ts* ze względu na pierwszym **extensionToExtension** reguły

* *Cart.js* nie jest zagnieżdżony w *cart.tsx* ponieważ **TS** poprzedzającej **.tsx** w zasadach, i może istnieć tylko jeden obiekt nadrzędny

* *Light.CSS* jest zagnieżdżony w *light.sass* ze względu na drugi **extensionToExtension** reguły

* *Home.HTML* jest zagnieżdżony w *home.md* ze względu na trzeci **extensionToExtension** reguły

### <a name="the-filesuffixtoextension-provider"></a>Dostawca fileSuffixToExtension

Ten dostawca działa podobnie jak **extensionToExtension** dostawcy, ale tylko różnica jest reguła porównaniem sufiks zamiast po prostu rozszerzenie pliku. Rozważmy następujący przykład:

![fileSuffixToExtension przykładowych reguł](media/filenesting_filesuffixtoextension.png) ![efekt przykład fileSuffixToExtension](media/filenesting_filesuffixtoextension_effect.png)

* *Portal vsdoc.js* jest zagnieżdżony w *portal.js* z powodu **fileSuffixToExtension** reguły

* każdy aspekt zasada działa tak samo jak **extensionToExtension**

### <a name="the-addedextension-provider"></a>Dostawca addedExtension

Ten dostawca zagnieżdżony pliki z rozszerzeniem dodatkowe w obszarze plik bez dodatkowego rozszerzenia. Dodatkowe rozszerzenia może wystąpić tylko na końcu Pełna nazwa pliku. Rozważmy następujący przykład:

![addedExtension przykładowych reguł](media/filenesting_addedextension.png) ![efekt przykład addedExtension](media/filenesting_addedextension_effect.png)

* *File.HTML.CSS* jest zagnieżdżony w *file.html* z powodu **addedExtension** reguły

### <a name="the-pathsegment-provider"></a>Dostawca pathSegment

Ten dostawca zagnieżdżony pliki z rozszerzeniem dodatkowe w obszarze plik bez dodatkowego rozszerzenia. Dodatkowe rozszerzenia może wystąpić tylko w środku Pełna nazwa pliku. Rozważmy następujący przykład:

![pathSegment przykładowych reguł](media/filenesting_pathsegment.png) ![efekt przykład pathSegment](media/filenesting_pathsegment_effect.png)

* *jquery.min.js* jest zagnieżdżony w *jquery.js* z powodu **pathSegment** reguły

### <a name="the-allextensions-provider"></a>Dostawca allExtensions

Ten dostawca pozwala zdefiniować reguły zagnieżdżenia pliku dla plików z dowolnego rozszerzenia, ale tej samej nazwie pliku podstawowego. Rozważmy następujący przykład:

![allExtensions przykładowych reguł](media/filenesting_allextensions.png) ![efekt przykład allExtensions](media/filenesting_allextensions_effect.png)

* *Template.cs* i *szablon.doc* są zagnieżdżone w obszarze *template.tt* z powodu **allExtensions** reguły.

### <a name="the-filetofile-provider"></a>Dostawca fileToFile

Ten dostawca pozwala zdefiniować reguły zagnieżdżenia pliku na podstawie całego nazw plików. Rozważmy następujący przykład:

![fileToFile przykładowych reguł](media/filenesting_filetofile.png) ![efekt przykład fileToFile](media/filenesting_filetofile_effect.png)

* *.bowerrc* jest zagnieżdżony w *bower.json* z powodu **fileToFile** reguły

### <a name="rule-order"></a>Kolejność reguł

Kolejność jest ważna w każdej części cyklu plik ustawień niestandardowych. Można zmienić kolejność, w której reguły są wykonywane, przenosząc je w górę lub w dół wewnątrz **dependentFileProvider** węzła. Na przykład, jeśli masz jedną regułę, która sprawia, że **file.js** elementem nadrzędnym **file.ts** i inną regułę, która sprawia, że **file.coffee** elementem nadrzędnym **file.ts**, kolejność, w jakiej występują w pliku decyduje o zagnieżdżenia zachowanie, gdy wszystkie trzy pliki. Ponieważ **file.ts** może mieć tylko jedną jednostkę nadrzędną, niezależnie od zasada wykonuje pierwszy serwer wins.

Kolejność jest również ważne dla reguły sekcjach, nie tylko pliki znajdujące się w sekcji. Zaraz po dopasowaniu parę plików z regułą zagnieżdżania plików innych reguł w dalszych szczegółów w pliku są ignorowane, a następnie dalej parę plików jest przetwarzany.

### <a name="file-nesting-button"></a>Przycisk zagnieżdżania plików

Możesz określić wszystkie ustawienia, w tym własne niestandardowe ustawienia, za pomocą tego samego przycisku w **Eksploratora rozwiązań**:

![Aktywuj niestandardowego pliku reguły zagnieżdżania](media/filenesting_activatecustom.png)

## <a name="create-solution-specific-and-project-specific-settings"></a>Tworzenie ustawień specyficznych dla rozwiązania i specyficznych dla projektu

Można utworzyć ustawień specyficznych dla rozwiązania i specyficznych dla projektu za pomocą menu kliknij prawym przyciskiem myszy (menu kontekstowe) każdego rozwiązania i projektu:

![Rozwiązanie i zagnieżdżenia reguły specyficzne dla projektu](media/filenesting_solutionprojectspecific.png)

Ustawienia specyficzne dla rozwiązania i specyficznych dla projektu są połączone z aktywne ustawienia programu Visual Studio. Na przykład może być plikiem puste ustawienia specyficzne dla projektu, ale **Eksploratora rozwiązań** nadal jest zagnieżdżanie plików. Zachowanie zagnieżdżenia pochodzi z ustawienia specyficzne dla rozwiązania lub ustawienia programu Visual Studio. Pierwszeństwo przed scaleniem ustawienia zagnieżdżania plików to: Visual Studio > Solution > Project.

Visual Studio, aby zignorować ustawień specyficznych dla rozwiązania i specyficznych dla projektu, można stwierdzić, nawet jeśli pliki znajdują się na dysku, włączając opcję **ignorowanie ustawień rozwiązania i projektu** w obszarze **narzędzia**  >  **Opcje** > **platformy ASP.NET Core** > **zagnieżdżanie plików**.

Można zrobić przeciwieństwo i przekaż programowi Visual Studio do *tylko* użyć określonego rozwiązania lub ustawienia specyficzne dla projektu, ustawiając **głównego** węzeł **true**. Visual Studio zatrzymuje scalanie plików na tym samym poziomie i nie łączyć ją z plikami wyżej hierarchii.

Ustawienia specyficzne dla rozwiązania i specyficznych dla projektu może zostać sprawdzone w kontroli źródła i całego zespołu działa na bazie kodu można udostępniać je.

## <a name="disable-global-file-nesting-rules-for-a-particular-solution-or-project"></a>Wyłączanie reguły zagnieżdżenia globalnego pliku dla danego rozwiązania lub projektu

Istniejące reguły zagnieżdżenia pliku globalnego dla określonych rozwiązań lub projektów, można wyłączyć za pomocą **Usuń** akcji dla dostawcy zamiast **Dodaj**. Na przykład jeśli dodasz następujący kod ustawień do projektu wszystkie **pathSegment** reguły, które mogą występować globalnie dla tego określonego projektu są wyłączone:

```json
"dependentFileProviders": {
  "remove": {
    "pathSegment": {}
  }
}
```

## <a name="see-also"></a>Zobacz także

- [Personalizowanie środowiska IDE](../ide/personalizing-the-visual-studio-ide.md)
