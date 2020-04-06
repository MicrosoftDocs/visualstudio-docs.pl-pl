---
title: Wdrażanie niestandardowych stron początkowych | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712229"
---
# <a name="deploy-custom-start-pages"></a>Wdrażanie niestandardowych stron początkowych

Niestandardowe strony startowe można wdrożyć przy użyciu wdrożenia VSIX lub przez skopiowanie plików do odpowiednich lokalizacji na komputerze docelowym.

## <a name="vsix-deployment-by-using-the-start-page-project-template"></a>Wdrożenie vsix przy użyciu szablonu projektu strona początkowa

Podczas tworzenia strony początkowej przy użyciu szablonu projektu strony początkowej, a następnie utworzyć projekt, Visual Studio tworzy plik *.vsix,* który można rozpowszechniać. Pakowanie strony początkowej w pliku *vsix* zapewnia następujące opcje wdrożenia, w zależności od zamierzonej grupy odbiorców:

- Plik *vsix* można umieścić w udziale sieciowym lub w publicznej witrynie sieci Web. Gdy ktoś otworzy plik, strona początkowa zostanie automatycznie zainstalowana.

- Plik *vsix* można przekazać do witryny sieci Web [programu Visual Studio Marketplace,](https://marketplace.visualstudio.com/) aby użytkownicy mogli go zainstalować za pomocą **Menedżera rozszerzeń**.

Szablon projektu Strona początkowa tworzy kopię domyślnej strony startowej programu Visual Studio, dzięki czemu można zmodyfikować kopię i zachować oryginał.

Szablon projektu Strona początkowa można uzyskać za pomocą **Menedżera rozszerzeń** lub pobierając go z witryny sieci Web.

## <a name="vsix-deployment-without-using-the-start-page-project-template"></a>Wdrożenie vsix bez użycia szablonu projektu Strona początkowa
 Pomyślne wdrożenie VSIX wymaga zainstalowania rozszerzenia w folderach rozpoznawanych przez proces rejestracji VSIX i przez **Menedżera rozszerzeń.** Ponieważ szablon projektu strony początkowej już określa poprawne foldery, zaleca się użycie go w dowolnym momencie, gdy chcesz spakować rozszerzenie do wdrożenia VSIX. Jednak jeśli masz przypadek, w którym nie można użyć szablonu, można utworzyć wdrożenie VSIX bez użycia go.

 Aby utworzyć wdrożenie VSIX bez użycia szablonu projektu strony początkowej, należy najpierw utworzyć plik *vsix* dla strony początkowej na jeden z następujących dwóch sposobów:

- Dodając niestandardowe pliki strony startowej do pustego projektu VSIX. Aby uzyskać więcej informacji, zobacz [szablon projektu VSIX](../extensibility/vsix-project-template.md).

- Ręcznie tworząc plik *vsix.* Aby ręcznie utworzyć plik *vsix:*

   1. Utwórz plik *extension.vsixmanifest* i *plik [Content_Types]. xml* w nowym folderze. Aby uzyskać więcej informacji, zobacz [Anatomia pakietu VSIX](../extensibility/anatomy-of-a-vsix-package.md).

   2. W Eksploratorze Windows kliknij prawym przyciskiem myszy folder zawierający dwa pliki XML, kliknij polecenie **Wyślij do**, a następnie kliknij polecenie Skompresowany (spakowany) folder. Zmień nazwę wynikowego pliku *zip* na *Filename.vsix*, gdzie Nazwa pliku jest nazwą redystrybucyjnego pliku, który instaluje pakiet.

Aby program Visual Studio rozpoznał `Content Element` stronę początkową, manifest `CustomExtension Element` VSIX `Type` musi zawierać `"StartPage"`atrybut, który ma ustawiony atrybut . Rozszerzenie strony początkowej, które zostało zainstalowane przy użyciu wdrożenia VSIX, pojawia się na liście **Dostosuj stronę startową** na stronie Opcje **uruchamiania** jako *nazwa rozszerzenia* **[Zainstalowane rozszerzenie].**

Jeśli pakiet strony początkowej zawiera zestawy, należy dodać rejestrację ścieżki powiązania, tak aby były one dostępne po uruchomieniu programu Visual Studio. Aby to zrobić, upewnij się, że pakiet zawiera plik *pkgdef,* który zawiera następujące informacje.

```
[$RootKey$\BindingPaths\{Insert a new GUID here}]
"$PackageFolder$"=""
```

### <a name="vsix-deployment-for-all-users"></a>Wdrożenie VSIX dla wszystkich użytkowników
 Domyślnie rozszerzenia wdrożone w pakietach VSIX są instalowane tylko dla bieżącego użytkownika. Stronę startową można zainstalować dla wszystkich użytkowników komputera docelowego, tworząc wdrożenie dla wszystkich użytkowników.

### <a name="to-create-an-all-users-deployment"></a>Aby utworzyć wdrożenie dla wszystkich użytkowników

1. Otwórz plik *extension.vsixmanifest* w widoku kodu.

2. W `Identifier` elemencie manifestu vsix dodaj element `AllUsers` `true`o wartości .

    ```
    <AllUsers>true</AllUsers>
    ```

     Powoduje to, że instalator vsix monituje o uprawnienia administratora, a następnie instaluje pliki do *\Common7\IDE\Extensions*.

3. Otwórz plik *pkgdef.*

4. Zmodyfikuj *plik pkgdef,* aby ustawić domyślną stronę początkową w obszarze HKLM, dodając następującą, gdzie *plik .xaml to* nazwa pliku *.xaml* zawierającego stronę początkową.

     [$RootKey$\StartPage\Default]

     "Uri"="$PackageFolder$\\*MyStartPage.xaml*"

     To informuje visual studio, aby spojrzeć w nowej lokalizacji strony początkowej.

## <a name="file-copy-deployment"></a>Wdrożenie kopii pliku
 Nie trzeba tworzyć pliku *vsix,* aby wdrożyć niestandardową stronę początkową. Zamiast tego można skopiować znaczniki i pliki pomocnicze bezpośrednio do <em>folderu \StartPages\* użytkownika. **Lista Dostosuj stronę początkową</em> * na stronie Opcje **uruchamiania** zawiera listę każdego pliku *xaml* w tym folderze wraz ze ścieżką — na przykład *%USERPROFILE%\Moje dokumenty\Visual Studio {wersja}\StartPages\\{Nazwa pliku}.xaml*. Jeśli strona początkowa zawiera odwołania do zestawów prywatnych, należy je skopiować i wkleić w folderze *\PrivateAssemblies.\*

 Aby rozpowszechniać stronę początkową utworzoną bez pakowania jej w pliku *vsix,* zaleca się użycie podstawowej strategii kopiowania plików, na przykład skryptu wsadowego lub innej technologii wdrażania, która umożliwia umieszczenie plików w wymaganych katalogach.

### <a name="to-manually-install-a-custom-start-page"></a>Aby ręcznie zainstalować niestandardową stronę startową

1. Skopiuj plik *.xaml zawierający* znacznik strony początkowej wraz z wszelkimi plikami pomocniczymi innymi niż\* zestawy i wklej je w folderze *\StartPages użytkownika.

2. Jeśli strona początkowa wymaga zestawów, skopiuj je i wklej w *pliku .. {Folder instalacyjny programu Visual Studio}\Common7\IDE\PrivateAssemblies\\. \\*

3. Na liście **Dostosowywanie strony początkowej** na stronie Opcje **uruchamiania** wybierz nową stronę początkową. Aby uzyskać więcej informacji, zobacz [Dostosowywanie strony początkowej](../ide/customizing-the-start-page-for-visual-studio.md).

## <a name="see-also"></a>Zobacz też

- [Dostosowywanie strony początkowej](../ide/customizing-the-start-page-for-visual-studio.md)
- [Dodawanie kontrolki użytkownika do strony początkowej](../extensibility/adding-user-control-to-the-start-page.md)
