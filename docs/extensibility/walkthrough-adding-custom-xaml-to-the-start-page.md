---
title: 'Przewodnik: Dodawanie niestandardowego kodu XAML do strony początkowej | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom start page
- xaml start page
ms.assetid: 9af4d5f9-1cfc-4221-aea7-c8cd3f7571a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 4e2afc90dc96978e8a8290afaa2d3278e8b621b3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697670"
---
# <a name="walkthrough-add-custom-xaml-to-the-start-page"></a>Instruktaż: Dodawanie niestandardowego kodu XAML do strony początkowej

W tym przewodniku pokazano, jak utworzyć niestandardową stronę początkową programu Visual Studio zawierającą przeglądarkę sieci Web.

## <a name="add-custom-xaml"></a>Dodawanie niestandardowego kodu XAML

1. Utwórz stronę początkową, postępując zgodnie z instrukcjami w [polu Utwórz niestandardową stronę początkową](../extensibility/creating-a-custom-start-page.md).

2. W pliku *MainWindow.xaml* znajdź \<sekcję> siatki.

3. Dodaj \<Element> TabControl i \<TabItem> wewnątrz \< Grid> element, jak pokazano w poniższym przykładzie.

    ```xml
    <Grid>
        <TabControl>
            <TabItem Header="Bing" Height="Auto">
                <Frame Source="http://www.bing.com" />
            </TabItem>
        </TabControl>
    </Grid>
    ```

4. Dodaj drugi \<> TabItem z \<button> element, który otwiera nowy projekt:

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

## <a name="test-the-custom-start-page"></a>Testowanie niestandardowej strony początkowej

1. Naciśnij klawisz **F5**.

     Zostanie otwarte eksperymentalne wystąpienie programu Visual Studio z zainstalowaną niestandardową stroną startową, ale nie wybraną.

2. W eksperymentalnym wystąpieniu programu Visual Studio otwórz stronę **Narzędzia /Opcje / Środowisko.**

3. Wybierz **pozycję Uruchamianie**. Na liście **Dostosowywanie strony początkowej** wybierz plik *xaml* i kliknij przycisk **OK**.

4. W menu **Widok** kliknij polecenie **Strona początkowa**.

5. Kliknij kartę **Bing.**

     Powinna zostać wyświetlona strona internetowa usługi Bing.

6. Kliknij kartę **Mój przycisk.**

     Powinien zostać wyświetlony przycisk **MyProject,** który otwiera okno dialogowe **Nowy projekt.**

7. Zamknij wystąpienie eksperymentalne.

Aby zastosować niestandardową stronę początkową, w **obszarze** > **Środowisko****opcji** > narzędzi wybierz pozycję **Startup**. Na liście **Dostosowywanie strony początkowej** wybierz plik *xaml* i kliknij przycisk **OK**.

## <a name="next-steps"></a>Następne kroki

Strona początkowa programu Visual Studio zawiera teraz kartę, na którym jest wyświetlana karta przeglądarka sieci Web i karta MyButton. Niestandardowe strony startowe, które mają inne funkcje, można utworzyć za pomocą modelu *zawierającego kod* w celu dodania niestandardowej biblioteki dll, jak pokazano w obszarze [Dodawanie sterowania użytkownikiem do strony początkowej](../extensibility/adding-user-control-to-the-start-page.md). Niestandardowe strony początkowe można udostępniać innym użytkownikom, publikując wynikowy plik vsix w witrynie sieci Web [programu Visual Studio Marketplace](https://marketplace.visualstudio.com/) lub w innej witrynie sieci Web lub udziale sieci Web. Aby uzyskać więcej informacji, zobacz [Wdrażanie niestandardowych stron startowych](../extensibility/deploying-custom-start-pages.md).

## <a name="see-also"></a>Zobacz też

- [Dostosowywanie strony początkowej](../ide/customizing-the-start-page-for-visual-studio.md)
- [Kontrolki kontenera WPF](https://msdn.microsoft.com/library/a0177167-d7db-4205-9607-8ae316952566)
