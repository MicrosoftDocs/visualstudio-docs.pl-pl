---
title: 'Wskazówki: Dodawanie niestandardowych XAML do strony początkowej | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- custom start page
- xaml start page
ms.assetid: 9af4d5f9-1cfc-4221-aea7-c8cd3f7571a6
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 58c7441a4f910a1da35bc464e12ddba3bd5583bc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51802528"
---
# <a name="walkthrough-adding-custom-xaml-to-the-start-page"></a>Przewodnik: dodawanie niestandardowych elementów XAML do strony początkowej
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym instruktażu przedstawiono sposób tworzenia niestandardowej programu Visual Studio strony początkowej zawierający przeglądarki sieci Web.  
  
## <a name="adding-custom-xaml"></a>Dodawanie niestandardowego XAML  
  
1.  Tworzenie strony początkowej, postępując zgodnie z instrukcjami w [tworzenie niestandardowe strony początkowej](../extensibility/creating-a-custom-start-page.md).  
  
2.  W pliku MainWindow.xaml Znajdź \<siatki > sekcji.  
  
3.  Dodaj \<TabControl > element i \<TabItem > wewnątrz \< siatki > elementu, jak pokazano w poniższym przykładzie.  
  
    ```xml  
    <Grid>  
        <TabControl>  
            <TabItem Header="Bing" Height="Auto">  
                <Frame Source="http://www.bing.com" />  
            </TabItem>  
        </TabControl>  
    </Grid>  
    ```  
  
4.  Dodaj drugą \<TabItem >, za pomocą \<przycisk > element, który zostanie otwarty nowy projekt:  
  
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
  
## <a name="testing-the-custom-start-page"></a>Testowanie niestandardową stronę początkową  
  
1.  Naciśnij F5.  
  
     Zostanie otwarty doświadczalnym wystąpieniu programu Visual Studio za pomocą niestandardowej strony początkowej zainstalowany, ale nie są wybrane.  
  
2.  W doświadczalnym wystąpieniu programu Visual Studio, otwórz **/Options narzędzia / środowisko** strony.  
  
3.  Wybierz **uruchamiania**. Na **Dostosuj stronę początkową** listy, wybierz swój plik .xaml, a następnie kliknij przycisk **OK**.  
  
4.  Na **widoku** menu, kliknij przycisk **strona startowa**.  
  
5.  Kliknij przycisk **Bing** kartę.  
  
     Powinna zostać wyświetlona strona sieci web Bing.  
  
6.  Kliknij przycisk **MyButton** kartę.  
  
     Powinien zostać wyświetlony **MyProject** przycisk, co spowoduje otwarcie **nowy projekt** okna dialogowego.  
  
7.  Zamknij wystąpienie doświadczalne.  
  
## <a name="applying-the-custom-start-page"></a>Stosowanie niestandardową stronę początkową  
  
#### <a name="to-test-the-custom-start-page"></a>Aby przetestować niestandardowej strony początkowej  
  
1.  W **narzędzia / Opcje / środowisko**, wybierz opcję **uruchamiania**. Na **Dostosuj stronę początkową** listy, wybierz swój plik .xaml, a następnie kliknij przycisk **OK**.  
  
## <a name="next-steps"></a>Następne kroki  
 Visual Studio strona początkowa zawiera teraz karta, która wyświetla kartę przeglądarki sieci Web i na karcie MyButton. Można tworzyć niestandardowe strony Start, mają inne funkcje za pomocą *związanym z kodem* model, aby dodać niestandardowy plik .dll, jak pokazano na [Dodawanie kontrolki użytkownika do strony początkowej](../extensibility/adding-user-control-to-the-start-page.md). Niestandardowe strony Start można udostępniać innym użytkownikom, publikując wynikowy plik .vsix do [galerii Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) witrynę sieci Web lub do innej witryny sieci Web lub udostępnianie. Aby uzyskać więcej informacji, zobacz [wdrażanie niestandardowych stron Start](../extensibility/deploying-custom-start-pages.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Dostosowanie strony początkowej](../ide/customizing-the-start-page-for-visual-studio.md)   
 [Kontrole kontenerów WPF](http://msdn.microsoft.com/en-us/a0177167-d7db-4205-9607-8ae316952566)

