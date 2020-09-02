---
title: 'Przewodnik: Dodawanie niestandardowego kodu XAML do strony startowej | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- custom start page
- xaml start page
ms.assetid: 9af4d5f9-1cfc-4221-aea7-c8cd3f7571a6
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7b2de492bd1eddf4bf18e4824cdb64de4241fa5f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65674112"
---
# <a name="walkthrough-adding-custom-xaml-to-the-start-page"></a>Przewodnik: dodawanie niestandardowych elementów XAML do strony początkowej
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym instruktażu pokazano, jak utworzyć niestandardową stronę początkową programu Visual Studio, która zawiera przeglądarkę internetową.  
  
## <a name="adding-custom-xaml"></a>Dodawanie niestandardowego kodu XAML  
  
1. Utwórz stronę początkową, postępując zgodnie z instrukcjami w temacie [Tworzenie niestandardowej strony początkowej](../extensibility/creating-a-custom-start-page.md).  
  
2. W pliku MainWindow. XAML Znajdź \<Grid> sekcję.  
  
3. Dodaj \<TabControl> element i \<TabItem> wewnątrz \< Grid> elementu, jak pokazano w poniższym przykładzie.  
  
    ```xml  
    <Grid>  
        <TabControl>  
            <TabItem Header="Bing" Height="Auto">  
                <Frame Source="http://www.bing.com" />  
            </TabItem>  
        </TabControl>  
    </Grid>  
    ```  
  
4. Dodaj drugi \<TabItem> , z \<Button> elementem otwierającym nowy projekt:  
  
    ```xml  
    <Grid>  
        <TabControl>  
            <TabItem Header="MyButton" Height="Auto">  
                <Button Name="btnNewProj" Content="New Project"   
                    Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
                    CommandParameter="File.NewProject" >  
                </Button>  
            </TabItem>  
            <TabItem Header="Bing" Height="Auto">  
                <Frame Source="http://www.bing.com" />  
            </TabItem>  
        </TabControl>  
    </Grid>  
    ```  
  
## <a name="testing-the-custom-start-page"></a>Testowanie niestandardowej strony początkowej  
  
1. Naciśnij F5.  
  
     Zostanie otwarte doświadczalne wystąpienie programu Visual Studio z zainstalowaną niestandardową stroną startową, ale nie została wybrana.  
  
2. W eksperymentalnym wystąpieniu programu Visual Studio Otwórz stronę **Narzędzia/Options/środowisko** .  
  
3. Wybierz pozycję **Uruchamianie**. Na liście **Dostosuj stronę początkową** wybierz plik XAML, a następnie kliknij przycisk **OK**.  
  
4. W menu **Widok** kliknij pozycję **Strona początkowa**.  
  
5. Kliknij kartę **Bing** .  
  
     Powinna zostać wyświetlona strona sieci Web Bing.  
  
6. Kliknij kartę Moje **przyciski** .  
  
     Powinien zostać wyświetlony przycisk "mój **projekt** ", który otwiera okno dialogowe **Nowy projekt** .  
  
7. Zamknij wystąpienie eksperymentalne.  
  
## <a name="applying-the-custom-start-page"></a>Stosowanie niestandardowej strony początkowej  
  
#### <a name="to-test-the-custom-start-page"></a>Aby przetestować niestandardową stronę początkową  
  
1. W obszarze **Narzędzia/Opcje/środowisko**wybierz pozycję **Uruchamianie**. Na liście **Dostosuj stronę początkową** wybierz plik XAML, a następnie kliknij przycisk **OK**.  
  
## <a name="next-steps"></a>Następne kroki  
 Strona startowa programu Visual Studio zawiera teraz kartę wyświetlającą kartę przeglądarki sieci Web i kartę z przyciskiem. Można utworzyć niestandardowe strony startowe, które mają inne funkcje przy użyciu modelu *związanego z kodem* do dodania pliku Custom. dll, jak pokazano w temacie [Dodawanie kontrolki użytkownika do strony Start](../extensibility/adding-user-control-to-the-start-page.md). Niestandardowe strony startowe można udostępniać innym użytkownikom, publikując plik. vsix w witrynie sieci Web [Visual Studio Marketplace](https://marketplace.visualstudio.com/) lub do innej witryny sieci Web lub udziału sieciowego. Aby uzyskać więcej informacji, zobacz [wdrażanie niestandardowych stron początkowych](../extensibility/deploying-custom-start-pages.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Dostosowywanie strony początkowej](../ide/customizing-the-start-page-for-visual-studio.md)   
 [Formanty kontenera WPF](https://msdn.microsoft.com/a0177167-d7db-4205-9607-8ae316952566)
