---
title: Wdrażanie niestandardowych stron początkowych | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package start page
- deploy start page
ms.assetid: 4a7eb360-de83-41d5-be53-3cfb160d19f9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 3f09f03a3404bbde346370149f210bf45e6e2306
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60078255"
---
# <a name="deploy-custom-start-pages"></a>Wdrażanie niestandardowych stron Start

Niestandardowe strony Start można wdrożyć za pomocą VSIX wdrażania lub kopiowania plików na poprawne lokalizacje na komputerze docelowym.

## <a name="vsix-deployment-by-using-the-start-page-project-template"></a>Wdrożenie VSIX przy użyciu szablonu projektu strona startowa

Podczas tworzenia strony początkowej przy użyciu szablonu projektu strony początkowej, a następnie skompilowanie projektu, Visual Studio tworzy *.vsix* pliku, którą można dystrybuować. Pakowanie strony początkowej w *.vsix* plików udostępnia następujące opcje wdrażania, w zależności od Twojego odbiorców:

- Możesz umieścić *.vsix* plik w udziale sieciowym lub w publicznej witrynie sieci Web. Gdy plik zostanie otwarty, strona startowa jest instalowana automatycznie.

- Możesz przekazać *.vsix* plik [Visual Studio Marketplace](https://marketplace.visualstudio.com/) witryny sieci Web, tak aby użytkownicy mogą zainstalować ją za pomocą **Menedżera rozszerzeń**.

Szablon projektu strona początkowa tworzy kopię domyślnego programu Visual Studio strony początkowej, można modyfikować, kopiować i zachować oryginalne.

Szablon projektu strona startowa można uzyskać za pomocą **Menedżera rozszerzeń** lub pobrać z witryny sieci Web.

## <a name="vsix-deployment-without-using-the-start-page-project-template"></a>Wdrożenie VSIX bez przy użyciu szablonu projektu strona startowa
 Pomyślne wdrożenie VSIX wymaga rozszerzenia do zainstalowania w folderach, które są rozpoznawane przez proces rejestracji VSIX i przez **Menedżera rozszerzeń**. Ponieważ szablon projektu strona startowa już określa prawidłowe foldery, zaleca się używać go zawsze wtedy, gdy chcesz pakietu rozszerzenia VSIX wdrożenia. Jednak jeśli przypadek, w której nie można użyć tego szablonu, można utworzyć wdrożenia VSIX bez korzystania z niego.

 Aby utworzyć wdrożenie VSIX bez przy użyciu szablonu projektu strony początkowej, należy najpierw utworzyć *.vsix* pliku strony początkowej w jeden z następujących dwóch sposobów:

- Dodając niestandardowe pliki strony początkowej do pusty projekt VSIX. Aby uzyskać więcej informacji, zobacz [szablonu projektu VSIX](../extensibility/vsix-project-template.md).

- Za pomocą ręcznego tworzenia *.vsix* pliku. Aby utworzyć *.vsix* pliku ręcznie:

   1. Tworzenie *extension.vsixmanifest* pliku i *[Content_Types] .xml* plik w nowym folderze. Aby uzyskać więcej informacji, zobacz [anatomia pakietu VSIX](../extensibility/anatomy-of-a-vsix-package.md).

   2. W Eksploratorze Windows, kliknij prawym przyciskiem myszy folder, który zawiera dwa pliki XML, kliknij przycisk **Wyślij do**, a następnie kliknij Folder skompresowany (zip). Zmień nazwę wynikowy *zip* plik *Filename.vsix*, gdzie nazwa_pliku to nazwa pliku pakietu redystrybucyjnego, który instaluje pakiet.

Dla programu Visual Studio, rozpoznawał strony początkowej `Content Element` manifestu VSIX musi zawierać `CustomExtension Element` zawierający `Type` ustawioną wartość atrybutu `"StartPage"`. Rozszerzenie strony początkowej, który został zainstalowany przy użyciu wdrożenia VSIX, który pojawia się w **Dostosuj stronę początkową** listy na **uruchamiania** Opcje strony jako **[zainstalowane rozszerzenie]** *Nazwa rozszerzenia*.

Jeśli pakiet strona początkowa zawiera zestawy, należy dodać powiązanie ścieżka rejestracji tak, aby były dostępne po uruchomieniu programu Visual Studio. Aby to zrobić, upewnij się, że pakiet zawiera *.pkgdef* pliku, który zawiera następujące informacje.

```
[$RootKey$\BindingPaths\{Insert a new GUID here}]
"$PackageFolder$"=""
```

### <a name="vsix-deployment-for-all-users"></a>Wdrożenie VSIX dla wszystkich użytkowników
 Domyślnie rozszerzenia wdrożone w pakietów VSIX instalować tylko dla bieżącego użytkownika. Istnieje możliwość instalacji strona startowa dla wszystkich użytkowników komputera docelowego, tworząc wdrożenia wszystkich użytkowników.

### <a name="to-create-an-all-users-deployment"></a>Aby utworzyć wdrożenie wszystkich użytkowników

1. Otwórz *extension.vsixmanifest* plików w widoku kodu.

2. W `Identifier` element manifestu vsix dodawania `AllUsers` element, który ma wartość `true`.

    ```
    <AllUsers>true</AllUsers>
    ```

     Powoduje to, że Instalator vsix monit o podanie uprawnień administratora, a następnie zainstalować pliki do *\Common7\IDE\Extensions*.

3. Otwórz *.pkgdef* pliku.

4. Modyfikowanie *.pkgdef* do ustawiania domyślnej strony początkowej w obszarze HKLM, dodając następujące polecenie, gdzie *MyStartPage.xaml* nazywa się *.xaml* pliku, który zawiera uruchamiania Strona.

     [$RootKey$\StartPage\Default]

     "Uri"="$PackageFolder$\\*MyStartPage.xaml*"

     Oznacza to, Visual Studio do wyszukania w nowej lokalizacji strony początkowej.

## <a name="file-copy-deployment"></a>Wdrażanie kopii plików
 Nie trzeba tworzyć *.vsix* plik, aby wdrożyć niestandardowej strony początkowej. Zamiast tego można kopiować znaczników i plików pomocniczych, bezpośrednio do użytkownika <em>\StartPages\* folderu. **Dostosuj stronę początkową</em>*  listy na **uruchamiania** Opcje strony wyświetla każdy *.xaml* plików w tym folderze, podając ścieżkę — na przykład *\StartPages Documents\Visual Studio {version} %USERPROFILE%\My\\{nazwa pliku} .xaml*. Jeśli strona początkowa zawiera odwołania do zestawów prywatnych, należy skopiować je i wklej je w * \PrivateAssemblies\* folderu.

 Aby dystrybuować strony początkowej, który został utworzony bez pakowanie w *.vsix* pliku, zaleca się użyć strategii kopiowania podstawowy plik, na przykład skryptu wsadowego, lub innej technologii wdrożenia, który pozwala umieścić pliki w wymagane katalogi.

### <a name="to-manually-install-a-custom-start-page"></a>Aby ręcznie zainstalować niestandardowej strony początkowej

1. Kopiuj *.xaml* pliku, który zawiera znaczniki strony początkowej, oraz wszelkie pliki pomocnicze, inne niż zestawy i wklej je w użytkownika * \StartPages\* folderu.

2. Jeśli strona startowa wymaga zestawów, skopiuj je i wklej je w *... \\\Common7\IDE\PrivateAssemblies {folder instalacji programu visual Studio}\\*.

3. W **Dostosuj stronę początkową** listy na **uruchamiania** opcji wybierz Nowa strona początkowa. Aby uzyskać więcej informacji, zobacz [Dostosuj stronę początkową](../ide/customizing-the-start-page-for-visual-studio.md).

## <a name="see-also"></a>Zobacz także

- [Dostosowanie strony początkowej](../ide/customizing-the-start-page-for-visual-studio.md)
- [Dodaj kontrolkę użytkownika do strony początkowej](../extensibility/adding-user-control-to-the-start-page.md)