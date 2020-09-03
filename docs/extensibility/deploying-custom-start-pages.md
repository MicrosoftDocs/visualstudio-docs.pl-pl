---
title: Wdrażanie niestandardowych stron początkowych | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package start page
- deploy start page
ms.assetid: 4a7eb360-de83-41d5-be53-3cfb160d19f9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 210b4589c0e2165af537c3fa9129affb06197e9b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712229"
---
# <a name="deploy-custom-start-pages"></a>Wdróż niestandardowe strony początkowe

Niestandardowe strony startowe można wdrożyć przy użyciu wdrożenia VSIX lub kopiując pliki do odpowiednich lokalizacji na komputerze docelowym.

## <a name="vsix-deployment-by-using-the-start-page-project-template"></a>Wdrożenie VSIX przy użyciu szablonu projektu Strona początkowa

Podczas tworzenia strony początkowej przy użyciu szablonu projektu Strona początkowa, a następnie kompilowania projektu, program Visual Studio tworzy plik *. vsix* , który można dystrybuować. Pakowanie strony początkowej w pliku *. vsix* zapewnia następujące możliwości wdrożenia, w zależności od zamierzonych odbiorców:

- Plik *VSIX* można umieścić w udziale sieciowym lub w publicznej witrynie sieci Web. Gdy ktoś otworzy plik, zostanie automatycznie zainstalowana Strona Start.

- Plik *. vsix* można przekazać do witryny sieci Web [Visual Studio Marketplace](https://marketplace.visualstudio.com/) , aby użytkownicy mogli ją zainstalować za pomocą **Menedżera rozszerzeń**.

Szablon projektu Strona początkowa tworzy kopię domyślnej strony początkowej programu Visual Studio, dzięki czemu można modyfikować kopię i zachować oryginał.

Szablon projektu strony początkowej można uzyskać za pomocą **Menedżera rozszerzeń** lub pobierając go z witryny sieci Web.

## <a name="vsix-deployment-without-using-the-start-page-project-template"></a>Wdrożenie VSIX bez użycia szablonu projektu strony początkowej
 Pomyślne wdrożenie VSIX wymaga zainstalowania rozszerzenia w folderach, które są rozpoznawane przez proces rejestracji VSIX i przez **Menedżera rozszerzeń**. Ponieważ szablon projektu strony startowej zawiera już poprawne foldery, zalecamy użycie go zawsze wtedy, gdy chcesz spakować rozszerzenie do wdrożenia VSIX. Jeśli jednak masz przypadek, w którym nie można użyć szablonu, możesz utworzyć wdrożenie VSIX bez użycia go.

 Aby utworzyć wdrożenie VSIX bez użycia szablonu projektu Strona początkowa, należy najpierw utworzyć plik *VSIX* dla strony Start na jeden z tych dwóch sposobów:

- Dodawanie niestandardowych plików strony początkowej do pustego projektu VSIX. Aby uzyskać więcej informacji, zobacz [szablon projektu VSIX](../extensibility/vsix-project-template.md).

- Przez ręczne utworzenie pliku *. vsix* . Aby ręcznie utworzyć plik *. vsix* :

   1. Utwórz plik *Extension. vsixmanifest* oraz plik *[Content_Types]. XML* w nowym folderze. Aby uzyskać więcej informacji, zobacz [Anatomia pakietu VSIX](../extensibility/anatomy-of-a-vsix-package.md).

   2. W Eksploratorze Windows kliknij prawym przyciskiem myszy folder zawierający dwa pliki XML, kliknij polecenie **Wyślij do**, a następnie kliknij folder skompresowany (zip). Zmień nazwę otrzymanego pliku *zip* na *filename. vsix*, gdzie filename to nazwa pliku redystrybucyjnego, który instaluje pakiet.

Aby program Visual Studio rozpoznał stronę początkową, `Content Element` manifest VSIX musi zawierać `CustomExtension Element` atrybut, który ma `Type` ustawioną wartość `"StartPage"` . Rozszerzenie strony początkowej, które zostało zainstalowane przy użyciu wdrożenia VSIX, pojawia się na liście **Dostosuj stronę początkową** na stronie opcje **uruchamiania** jako *nazwa rozszerzenia* **[zainstalowane rozszerzenie]** .

Jeśli pakiet strony początkowej zawiera zestawy, należy dodać rejestrację ścieżki powiązania, aby była dostępna podczas uruchamiania programu Visual Studio. W tym celu należy się upewnić, że pakiet zawiera plik *. pkgdef* , który zawiera następujące informacje.

```
[$RootKey$\BindingPaths\{Insert a new GUID here}]
"$PackageFolder$"=""
```

### <a name="vsix-deployment-for-all-users"></a>Wdrożenie VSIX dla wszystkich użytkowników
 Domyślnie rozszerzenia wdrożone w pakietach VSIX instalują tylko dla bieżącego użytkownika. Możesz wykonać instalację strony startowej dla wszystkich użytkowników maszyny docelowej, tworząc wdrożenie wszyscy użytkownicy.

### <a name="to-create-an-all-users-deployment"></a>Aby utworzyć wdrożenie wszystkich użytkowników

1. Otwórz plik *Extension. vsixmanifest* w widoku kodu.

2. W `Identifier` elemencie manifestu VSIX Dodaj `AllUsers` element, który ma wartość `true` .

    ```
    <AllUsers>true</AllUsers>
    ```

     Powoduje to wyświetlenie monitu Instalatora VSIX o uprawnienia administratora, a następnie zainstalowanie plików w *\Common7\IDE\Extensions*.

3. Otwórz plik *. pkgdef* .

4. Zmodyfikuj plik *. pkgdef* , aby ustawić domyślną stronę początkową w obszarze HKLM, dodając następujące polecenie, gdzie *webstartpage. XAML* jest nazwą pliku *XAML* , który zawiera stronę początkową.

     [$RootKey $ \StartPage\Default]

     "URI" = "$PackageFolder $ \\ *Startpage. XAML*"

     To nakazuje programowi Visual Studio wyszukanie nowej lokalizacji strony początkowej.

## <a name="file-copy-deployment"></a>Wdrożenie kopiowania plików
 Nie ma potrzeby tworzenia pliku *. vsix* w celu wdrożenia niestandardowej strony początkowej. Zamiast tego można skopiować znaczniki i pliki pomocnicze bezpośrednio do <em>folderu \StartPages użytkownika \* . Na liście **Dostosuj stronę początkową</em> * na stronie opcje **uruchamiania** znajduje się każdy plik *XAML* w tym folderze wraz ze ścieżką — na przykład *%USERPROFILE%\My Documents\Visual Studio {Version} \StartPages \\ {File Name}. XAML*. Jeśli strona początkowa zawiera odwołania do zestawów prywatnych, należy je skopiować i wkleić do folderu * \PrivateAssemblies \* .

 Aby dystrybuować stronę początkową utworzoną bez pakowania jej w pliku *. vsix* , zalecamy użycie podstawowej strategii kopiowania plików, na przykład skryptu wsadowego, lub dowolnej innej technologii wdrażania, która umożliwia umieszczenie plików w wymaganych katalogach.

### <a name="to-manually-install-a-custom-start-page"></a>Aby ręcznie zainstalować niestandardową stronę początkową

1. Skopiuj plik *XAML* , który zawiera znaczniki strony początkowej, razem z innymi plikami pomocniczymi innymi niż zestawy, a następnie wklej je w folderze * \StartPages użytkownika \* .

2. Jeśli strona początkowa wymaga zestawów, skopiuj je i wklej w *.. \\ {Folder instalacyjny programu Visual Studio} \\ \Common7\IDE\PrivateAssemblies*.

3. Na liście **Dostosuj stronę początkową** na stronie opcje **uruchamiania** wybierz nową stronę początkową. Aby uzyskać więcej informacji, zobacz [Dostosowywanie strony początkowej](../ide/customizing-the-start-page-for-visual-studio.md).

## <a name="see-also"></a>Zobacz też

- [Dostosuj stronę początkową](../ide/customizing-the-start-page-for-visual-studio.md)
- [Dodawanie kontrolki użytkownika do strony początkowej](../extensibility/adding-user-control-to-the-start-page.md)
