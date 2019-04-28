---
title: 'Przewodnik: Dodawanie niestandardowych XAML do strony początkowej | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom start page
- xaml start page
ms.assetid: 9af4d5f9-1cfc-4221-aea7-c8cd3f7571a6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 2ee368224eb4991a2f1f167d565bd2b07f85d4c6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62953078"
---
# <a name="walkthrough-add-custom-xaml-to-the-start-page"></a>Przewodnik: Dodaj niestandardowe XAML do strony początkowej

W tym instruktażu przedstawiono sposób tworzenia niestandardowej strony początkowej programu Visual Studio, zawierający przeglądarki sieci Web.

## <a name="add-custom-xaml"></a>Dodaj niestandardowe XAML

1. Utwórz stronę początkową, postępując zgodnie z instrukcjami wyświetlanymi w [utworzyć niestandardową stronę początkową](../extensibility/creating-a-custom-start-page.md).

2. W *MainWindow.xaml* plików, Znajdź \<siatki > sekcji.

3. Dodaj \<TabControl > element i \<TabItem > wewnątrz \< siatki > elementu, jak pokazano w poniższym przykładzie.

    ```xml
    <Grid>
        <TabControl>
            <TabItem Header="Bing" Height="Auto">
                <Frame Source="http://www.bing.com" />
            </TabItem>
        </TabControl>
    </Grid>
    ```

4. Dodaj drugą \<TabItem >, za pomocą \<przycisk > element, który zostanie otwarty nowy projekt:

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

## <a name="test-the-custom-start-page"></a>Testowanie niestandardową stronę początkową

1. Naciśnij klawisz **F5**.

     Zostanie otwarta doświadczalnym wystąpieniu programu Visual Studio z niestandardową stronę początkową zainstalowany, ale nie są wybrane.

2. W doświadczalnym wystąpieniu programu Visual Studio, otwórz **/Options narzędzia / środowisko** strony.

3. Wybierz **uruchamiania**. Na **Dostosuj stronę początkową** listy wybierz swoje *.xaml* pliku, a następnie kliknij przycisk **OK**.

4. Na **widoku** menu, kliknij przycisk **strona startowa**.

5. Kliknij przycisk **Bing** kartę.

     Powinna zostać wyświetlona strona sieci web Bing.

6. Kliknij przycisk **MyButton** kartę.

     Powinien zostać wyświetlony **MyProject** przycisk, co spowoduje otwarcie **nowy projekt** okna dialogowego.

7. Zamknij wystąpienie doświadczalne.

Aby zastosować niestandardową stronę początkową, **narzędzia** > **opcje** > **środowiska**, wybierz opcję **uruchamiania**. Na **Dostosuj stronę początkową** listy wybierz swoje *.xaml* pliku, a następnie kliknij przycisk **OK**.

## <a name="next-steps"></a>Następne kroki

Strona początkowa programu Visual Studio zawiera teraz karta, która wyświetla kartę przeglądarki sieci Web i na karcie MyButton. Można tworzyć niestandardowych stron początkowych, które mają inne funkcje za pomocą *związanym z kodem* model, aby dodać niestandardowy plik .dll, jak pokazano na [Dodawanie kontrolki użytkownika do strony początkowej](../extensibility/adding-user-control-to-the-start-page.md). Niestandardowych stron początkowych można udostępniać innym użytkownikom, publikując wynikowy plik .vsix do [Visual Studio Marketplace](https://marketplace.visualstudio.com/) witrynę sieci Web lub do innej witryny sieci Web lub udostępnianie. Aby uzyskać więcej informacji, zobacz [wdrażanie niestandardowych stron Start](../extensibility/deploying-custom-start-pages.md).

## <a name="see-also"></a>Zobacz także

- [Dostosuj stronę początkową](../ide/customizing-the-start-page-for-visual-studio.md)
- [Kontrole kontenerów WPF](https://msdn.microsoft.com/library/a0177167-d7db-4205-9607-8ae316952566)