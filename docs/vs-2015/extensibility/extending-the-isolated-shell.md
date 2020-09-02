---
title: Rozszerzanie izolowanej powłoki | Microsoft Docs
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
ms.openlocfilehash: ea55039de769598b26868727a93cfa11726e4838
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64799318"
---
# <a name="extending-the-isolated-shell"></a>Rozszerzanie programu Shell (izolowanego)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można rozwinąć izolowaną powłokę programu Visual Studio, dodając składnik pakietu VSPackage, część składnika Managed Extensibility Framework (MEF) lub ogólny projekt VSIX do aplikacji powłoki izolowanej.  
  
> [!NOTE]
> Poniższe kroki presuppose, że utworzono podstawową izolowaną aplikację powłoki przy użyciu szablonu projektu izolowanego programu Visual Studio Shell. Aby uzyskać więcej informacji na temat tego szablonu projektu, zobacz [Przewodnik: Tworzenie podstawowej aplikacji powłoki izolowanej](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Lokalizacje szablonu projektu pakietu programu Visual Studio  
 Szablon projektu pakietu programu Visual Studio można znaleźć w trzech różnych lokalizacjach w oknie dialogowym **Nowy projekt** :  
  
1. W **Visual Basic**obszarze Visual Basic **rozszerzanie**. Domyślny język projektu jest Visual Basic.  
  
2. W obszarze **Visual C#**, **rozszerzalność**. Językiem domyślnym projektu jest C#.  
  
3. W obszarze **Inne typy projektów**, **rozszerzalność**. Językiem domyślnym projektu jest C++.  
  
## <a name="adding-a-vspackage"></a>Dodawanie elementu pakietu VSPackage  
 Można dodać pakietu VSPackage do aplikacji powłoki izolowanej. Poniższe kroki pokazują, jak utworzyć jeden, który dodaje polecenia menu.  
  
#### <a name="to-add-a-new-vspackage"></a>Aby dodać nowy pakietu VSPackage  
  
1. Dodaj projekt pakietu programu Visual Studio o nazwie `MenuCommandsPackage` .  
  
2. Na stronie **podstawowe informacje pakietu VSPackage** kreatora Ustaw **nazwę firmy** na `Fabrikam` i **pakietu VSPackage** na `FabrikamMenuCommands` . Wybierz przycisk **dalej** .  
  
3. Na następnej stronie wybierz **polecenie menu** , a następnie wybierz polecenie **dalej**.  
  
4. Na następnej stronie Ustaw **nazwę polecenia** na `Fabrikam Command` i **Identyfikator polecenia** na `cmdidFabrikamCommand` , a następnie wybierz przycisk **dalej**.  
  
5. Na stronie **Wybierz opcje projektu testowego** Wyczyść Opcje testu, a następnie wybierz przycisk **Zakończ** .  
  
6. W projekcie ShellExtensionsVSIX Otwórz plik source. Extension. vsixmanifest.  
  
     Sekcja **Assets** powinna zawierać wpis dla projektu VSShellStub. AboutBoxPackage.  
  
7. Wybierz przycisk **Nowy** .  
  
8. W oknie **Dodaj nowe zasoby** na liście **Typ** wybierz pozycję **Microsoft. VisualStudio. pakietu VSPackage**.  
  
9. Upewnij się, że na liście **Źródło** jest zaznaczony **projekt w bieżącym rozwiązaniu** . W polu Lista **projektu** wybierz pozycję **MenuCommandsPackage**.  
  
10. Zapisz i zamknij plik.  
  
11. Skompiluj ponownie rozwiązanie i Rozpocznij debugowanie izolowanej powłoki.  
  
12. Na pasku menu wybierz menu **Narzędzia** , a następnie **polecenie Fabrikam**.  
  
     Powinno zostać wyświetlone okno komunikatu.  
  
13. Zatrzymaj debugowanie aplikacji.  
  
## <a name="adding-a-mef-component-part"></a>Dodawanie części składnika MEF  
 Poniższe kroki pokazują, jak dodać część składnika MEF do aplikacji izolowanej powłoki.  
  
#### <a name="to-add-a-mef-component"></a>Aby dodać składnik MEF  
  
1. W oknie dialogowym **Dodaj nowy projekt** w obszarze **Visual C#**, **rozszerzalność**, użyj szablonu **marginesu edytora** , aby dodać projekt. Nadaj jej nazwę `ShellEditorMargin`.  
  
2. W projekcie ShellExtensionsVSIX Otwórz plik source. Extension. vsixmanifest w widok Projekt, a nie widok kodu.  
  
3. W `Asset` sekcji Wybierz pozycję **Dodaj zawartość**.  
  
4. W oknie **Dodaj nowe zasoby** na liście **Typ** wybierz pozycję **Microsoft. VisualStudio. MefComponent**.  
  
5. Upewnij się, że na liście **Źródło** jest zaznaczony **projekt w bieżącym rozwiązaniu** . W polu Lista **projektu** wybierz pozycję **ShellEditorMargin**.  
  
6. Zapisz i zamknij plik.  
  
7. Skompiluj ponownie rozwiązanie i Rozpocznij debugowanie izolowanej powłoki.  
  
8. Otwórz plik tekstowy.  
  
     Zielony margines zawierający słowa "Hello World!" powinna być wyświetlana u dołu okna plik tekstowy.  
  
9. Zatrzymaj debugowanie aplikacji.  
  
## <a name="adding-a-generic-vsix-project"></a>Dodawanie ogólnego projektu VSIX  
  
#### <a name="to-add-a-generic-vsix-project"></a>Aby dodać ogólny projekt VSIX  
  
1. W oknie dialogowym **Dodaj nowy projekt** w obszarze **Visual C#**, **rozszerzalność**, użyj szablonu **VSIXProject** , aby dodać projekt. Nadaj jej nazwę `EmptyVSIX`.  
  
2. W projekcie ShellExtensionsVSIX Otwórz plik source. Extensions. vsixmanifest w widok Projekt, a nie widok kodu.  
  
3. W `Assets` sekcji Wybierz pozycję **Nowy**.  
  
4. W oknie **Dodaj nowe zasoby** na liście **Typ** wybierz rodzaj zawartości, którą chcesz dodać.  
  
5. W obszarze **Źródło**upewnij się, że jest zaznaczona opcja **projekt w bieżącym rozwiązaniu** . W polu listy wybierz nazwę projektu VSIX.  
  
6. Zapisz i zamknij plik.  
  
7. Jeśli ten projekt zawiera skompilowany kod, należy edytować projekt, tak aby zestaw został uwzględniony w danych wyjściowych.  
  
    1. Zwolnij projekt VSIX i Otwórz plik projektu.  
  
    2. W pierwszym `<PropertyGroup>` bloku Zmień wartość `<CopyBuildOutputToOutputDirectory>` na `true` .  
  
    3. Zapisz i Załaduj ponownie projekt.  
  
8. Skompiluj i uruchom rozwiązanie.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: Tworzenie podstawowej aplikacji Isolated Shell](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)
