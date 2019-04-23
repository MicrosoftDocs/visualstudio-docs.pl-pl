---
title: Rozszerzanie programu Isolated Shell | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode
ms.assetid: 9a641d8f-211e-4486-a1b1-4a89fafe7ee8
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 65efd5a864863fb18f26d8fdfc3736423aad7aeb
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60054095"
---
# <a name="extending-the-isolated-shell"></a>Rozszerzanie programu Isolated Shell
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Powłoka programu Visual Studio, izolowany można rozszerzyć przez dodanie pakietu VSPackage, część Managed Extensibility Framework (MEF) lub ogólny projekt VSIX do Twojej aplikacji isolated shell.  
  
> [!NOTE]
>  Poniższe kroki zakładają, że utworzono podstawowej aplikacji isolated shell przy użyciu programu Visual Studio Shell izolowane szablonu projektu. Aby uzyskać więcej informacji na temat tego szablonu projektu, zobacz [instruktażu: Tworzenie prostej Isolated Shell aplikacji](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Lokalizacje szablon projektu pakietu Visual Studio  
 Szablon projektu pakietu Visual Studio można znaleźć w trzech różnych miejscach w **nowy projekt** okno dialogowe:  
  
1. W obszarze **języka Visual Basic**, **rozszerzalności**. Domyślny język projektu jest języka Visual Basic.  
  
2. W obszarze **Visual C#**, **rozszerzalności**. Domyślny język projektu jest C#.  
  
3. W obszarze **innych typów projektów**, **rozszerzalności**. Domyślny język projektu jest w języku C++.  
  
## <a name="adding-a-vspackage"></a>Dodawanie pakietu VSPackage  
 Pakietu VSPackage można dodać do swojej aplikacji isolated shell. Poniższe kroki pokazują jak utworzyć klucz, który dodaje poleceń menu.  
  
#### <a name="to-add-a-new-vspackage"></a>Aby dodać nowego pakietu VSPackage  
  
1. Dodaj projekt pakietu Visual Studio o nazwie `MenuCommandsPackage`.  
  
2. Na **podstawowe informacje pakietu VSPackage** strony kreatora, ustaw **nazwa firmy** do `Fabrikam` i **nazwa pakietu VSPackage** do `FabrikamMenuCommands`. Wybierz **dalej** przycisku.  
  
3. Na następnej stronie wybierz **polecenia Menu** , a następnie wybierz **dalej**.  
  
4. Na następnej stronie Ustaw **nazwa polecenia** do `Fabrikam Command` i **identyfikator polecenia** do `cmdidFabrikamCommand`, a następnie wybierz **dalej**.  
  
5. Na **opcje projektu testów wybierz** strony, usuń zaznaczenie opcji testowania, a następnie wybierz **Zakończ** przycisku.  
  
6. W projekcie ShellExtensionsVSIX Otwórz plik source.extension.vsixmanifest.  
  
     **Zasoby** sekcji może zawierać wpis dla projektu VSShellStub.AboutBoxPackage.  
  
7. Wybierz **New** przycisku.  
  
8. W **Dodaj nowy zasób** okna w **typu** listy wybierz **Microsoft.VisualStudio.VsPackage**.  
  
9. W **źródła** listy, upewnij się, że **projektu w bieżącym rozwiązaniu** jest zaznaczone. W **projektu** pola listy, wybierz opcję **MenuCommandsPackage**.  
  
10. Zapisz i zamknij plik.  
  
11. Ponownie skompiluj rozwiązanie, a następnie rozpocząć debugowanie programu isolated shell.  
  
12. Na pasku menu wybierz **narzędzia** menu, a następnie **polecenia Fabrikam**.  
  
     Powinna pojawić się okno komunikatu.  
  
13. Zatrzymaj debugowanie aplikacji.  
  
## <a name="adding-a-mef-component-part"></a>Dodając część MEF  
 Poniższe kroki pokazują jak dodać składnik MEF do Twojej aplikacji isolated shell.  
  
#### <a name="to-add-a-mef-component"></a>Aby dodać składnik MEF  
  
1. W **Dodaj nowy projekt** dialogowego **Visual C#**, **rozszerzalności**, użyj **marginesu edytora** szablon, aby dodać projekt. Nadaj mu nazwę `ShellEditorMargin`.  
  
2. W projekcie ShellExtensionsVSIX Otwórz plik Source.extension.vsixmanifest w widoku Projekt, a nie widoku kodu.  
  
3. W `Asset` wybierz pozycję **Dodaj zawartość**.  
  
4. W **Dodaj nowy zasób** okna w **typu** listy wybierz **Microsoft.VisualStudio.MefComponent**.  
  
5. W **źródła** listy, upewnij się, że **projektu w bieżącym rozwiązaniu** jest zaznaczone. W **projektu** pola listy, wybierz opcję **ShellEditorMargin**.  
  
6. Zapisz i zamknij plik.  
  
7. Ponownie skompiluj rozwiązanie, a następnie rozpocząć debugowanie programu isolated shell.  
  
8. Otwórz plik tekstowy.  
  
     Margines zielony, który zawiera słowa "Hello world!" powinny być wyświetlane w dolnej części okna pliku tekstowego.  
  
9. Zatrzymaj debugowanie aplikacji.  
  
## <a name="adding-a-generic-vsix-project"></a>Dodawanie projektu VSIX ogólny  
  
#### <a name="to-add-a-generic-vsix-project"></a>Aby dodać ogólny projekt VSIX  
  
1. W **Dodaj nowy projekt** dialogowego **Visual C#**, **rozszerzalności**, użyj **VSIXProject** szablon, aby dodać projekt. Nadaj mu nazwę `EmptyVSIX`.  
  
2. W projekcie ShellExtensionsVSIX Otwórz plik Source.extensions.vsixmanifest w widoku Projekt, a nie widoku kodu.  
  
3. W `Assets` wybierz pozycję **New**.  
  
4. W **Dodaj nowy zasób** okna w **typu** listy, wybierz typ zawartości, którą chcesz dodać.  
  
5. W **źródła**, upewnij się, że **projekt w bieżącym rozwiązaniu** opcja jest zaznaczona. W polu listy wybierz nazwę projektu VSIX.  
  
6. Zapisz i zamknij plik.  
  
7. Jeśli ten projekt zawiera kod skompilowany, należy zmodyfikować projekt tak, aby zestaw znajduje się w danych wyjściowych.  
  
    1. Zwolnij projekt VSIX, a następnie otwórz plik projektu.  
  
    2. W pierwszym `<PropertyGroup>` zablokować, zmień wartość właściwości `<CopyBuildOutputToOutputDirectory>` do `true`.  
  
    3. Zapisz i ponownie Załaduj projekt.  
  
8. Skompiluj i uruchom rozwiązanie.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: Tworzenie podstawowej aplikacji Isolated Shell](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)
