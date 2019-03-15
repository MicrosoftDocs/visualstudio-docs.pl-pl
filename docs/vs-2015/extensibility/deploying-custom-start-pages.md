---
title: Wdrażanie niestandardowych stron początkowych | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- package start page
- deploy start page
ms.assetid: 4a7eb360-de83-41d5-be53-3cfb160d19f9
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dcf653654005b75a889bcafd668fbb9313572ff2
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57867115"
---
# <a name="deploying-custom-start-pages"></a>Wdrażanie niestandardowych stron początkowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Niestandardowe strony Start można wdrożyć za pomocą VSIX wdrażania lub kopiowania plików na poprawne lokalizacje na komputerze docelowym.  
  
## <a name="vsix-deployment-by-using-the-start-page-project-template"></a>Wdrożenie VSIX przy użyciu szablonu projektu strona uruchamiania  
 Podczas tworzenia strony początkowej przy użyciu szablonu projektu strony początkowej, a następnie skompilowanie projektu, Visual Studio tworzy plik .vsix, którą można dystrybuować. Pakowanie strony początkowej, w pliku .vsix zapewnia następujące opcje wdrażania, w zależności od Twojego odbiorców:  
  
- Możesz umieścić plik .vsix, w udziale sieciowym lub w publicznej witrynie sieci Web. Gdy plik zostanie otwarty, strona startowa jest instalowana automatycznie.  
  
- Możesz przekazać plik .vsix do [Visual Studio Marketplace](https://marketplace.visualstudio.com/) witryny sieci Web, tak aby użytkownicy mogą zainstalować ją za pomocą **Menedżera rozszerzeń**.  
  
  Szablon projektu strona początkowa tworzy kopię domyślnego programu Visual Studio strony początkowej, można modyfikować, kopiować i zachować oryginalne.  
  
  Szablon projektu strona startowa można uzyskać za pomocą **Menedżera rozszerzeń** lub pobrać z witryny sieci Web.  
  
## <a name="vsix-deployment-without-using-the-start-page-project-template"></a>Wdrożenie VSIX bez przy użyciu szablonu projektu strona uruchamiania  
 Pomyślne wdrożenie VSIX wymaga rozszerzenia do zainstalowania w folderach, które są rozpoznawane przez proces rejestracji VSIX i przez **Menedżera rozszerzeń**. Ponieważ szablon projektu strona startowa już określa prawidłowe foldery, zaleca się używać go zawsze wtedy, gdy chcesz pakietu rozszerzenia VSIX wdrożenia. Jednak jeśli przypadek, w której nie można użyć tego szablonu, można utworzyć wdrożenia VSIX bez korzystania z niego.  
  
 Aby utworzyć wdrożenie VSIX bez przy użyciu szablonu projektu strony początkowej, należy najpierw utworzyć plik .vsix dla strony początkowej w jeden z następujących dwóch sposobów:  
  
- Dodając niestandardowe pliki strony początkowej do pusty projekt VSIX. Aby uzyskać więcej informacji, zobacz [szablonu projektu VSIX](../extensibility/vsix-project-template.md).  
  
- Za pomocą ręcznego tworzenia pliku .vsix. Aby uzyskać więcej informacji, zobacz [jak: Ręcznie pakietu rozszerzenia (VSIX wdrożenie)](../misc/how-to-manually-package-an-extension-vsix-deployment.md).  
  
  Dla programu Visual Studio, rozpoznawał strony początkowej `Content Element` manifestu VSIX musi zawierać `CustomExtension Element` zawierający `Type` ustawioną wartość atrybutu `"StartPage"`. Rozszerzenie strony początkowej, który został zainstalowany przy użyciu wdrożenia VSIX, który pojawia się w **Dostosuj stronę początkową** listy na **uruchamiania** Opcje strony jako **[zainstalowane rozszerzenie]** *Nazwa rozszerzenia*.  
  
  Jeśli pakiet strona początkowa zawiera zestawy, należy dodać powiązanie ścieżka rejestracji tak, aby były dostępne po uruchomieniu programu Visual Studio. Aby to zrobić, upewnij się, że pakiet zawiera plik .pkgdef, który zawiera następujące informacje.  
  
```  
[$RootKey$\BindingPaths\{Insert a new GUID here}]  
"$PackageFolder$"=""  
```  
  
### <a name="vsix-deployment-for-all-users"></a>Wdrożenie VSIX dla wszystkich użytkowników  
 Domyślnie rozszerzenia wdrożone w pakietów VSIX instalować tylko dla bieżącego użytkownika. Istnieje możliwość instalacji strona startowa dla wszystkich użytkowników komputera docelowego, tworząc wdrożenia wszystkich użytkowników.  
  
##### <a name="to-create-an-all-users-deployment"></a>Aby utworzyć wdrożenie wszystkich użytkowników  
  
1.  Otwórz plik extension.vsixmanifest w widoku kodu.  
  
2.  W `Identifier` element manifestu vsix dodawania `AllUsers` element, który ma wartość `true`.  
  
    ```  
    <AllUsers>true</AllUsers>  
    ```  
  
     To powoduje, że Instalator vsix monit o podanie uprawnień administratora, a następnie zainstalować pliki do \Common7\IDE\Extensions.  
  
3.  Otwórz plik .pkgdef.  
  
4.  Modyfikowanie .pkgdef do ustawiania domyślnej strony początkowej w obszarze HKLM, dodając następujące polecenie, gdzie *MyStartPage.xaml* jest nazwą pliku XAML, który zawiera stronę początkową.  
  
     [$RootKey$\StartPage\Default]  
  
     "Uri"="$PackageFolder$\\*MyStartPage.xaml*"  
  
     Oznacza to, umieszczenia Visual do wyszukania w nowej lokalizacji strony początkowej.  
  
## <a name="file-copy-deployment"></a>Wdrażanie kopii plików  
 Nie trzeba utworzyć plik .vsix, aby wdrożyć niestandardowej strony początkowej. Zamiast tego możesz skopiować znaczników i towarzyszące mu pliki bezpośrednio w folderze \StartPages\ użytkownika. **Dostosuj stronę początkową** listy na **uruchamiania** Strona opcji listę wszystkich plików .xaml w tym folderze, podając ścieżkę — na przykład %USERPROFILE%\My Documents\Visual Studio  *Wersja*\StartPages\\*nazwy pliku*.xaml. Jeśli strona początkowa zawiera odwołania do zestawów prywatnych, należy skopiować je i wklej je w folderze \PrivateAssemblies\.  
  
 Do dystrybucji strony początkowej, który został utworzony bez opakowania go w pliku .vsix, zaleca się że Użyj strategii kopiowanie podstawowego pliku, na przykład skrypt wsadowy lub inne technologie wdrażania, która umożliwia umieścić pliki w katalogach wymagane.  
  
#### <a name="to-manually-install-a-custom-start-page"></a>Aby ręcznie zainstalować niestandardowej strony początkowej  
  
1.  Skopiuj plik .xaml, który zawiera znaczniki strony początkowej, oraz wszelkie pliki pomocnicze, inne niż zestawy i wklej je w folderze \StartPages\ użytkownika.  
  
2.  Jeśli strona startowa wymaga zestawów, skopiuj je i wklej je w... \\ *Folder instalacji programu visual Studio*\Common7\IDE\PrivateAssemblies\\.  
  
3.  W **Dostosuj stronę początkową** listy na **uruchamiania** opcji wybierz Nowa strona początkowa. Aby uzyskać więcej informacji, zobacz [Dostosowywanie strony początkowej](../ide/customizing-the-start-page-for-visual-studio.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Dostosowanie strony początkowej](../ide/customizing-the-start-page-for-visual-studio.md)   
 [Dodawanie kontrolki użytkownika do strony początkowej](../extensibility/adding-user-control-to-the-start-page.md)
