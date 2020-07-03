---
title: 'Przewodnik: Dodawanie niestandardowego kodu XAML do strony startowej | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: a13aada6cca9b54d8469885ab4c314a89cd06d6c
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905966"
---
# <a name="walkthrough-add-custom-xaml-to-the-start-page"></a>Przewodnik: Dodawanie niestandardowego kodu XAML do strony początkowej

W tym instruktażu pokazano, jak utworzyć niestandardową stronę początkową programu Visual Studio, która zawiera przeglądarkę internetową.

## <a name="add-custom-xaml"></a>Dodaj niestandardowy kod XAML

1. Utwórz stronę początkową, postępując zgodnie z instrukcjami podanymi w temacie [Tworzenie niestandardowej strony początkowej](../extensibility/creating-a-custom-start-page.md).

2. W pliku *MainWindow. XAML* Znajdź \<Grid> sekcję.

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

## <a name="test-the-custom-start-page"></a>Testowanie niestandardowej strony początkowej

1. Naciśnij klawisz **F5**.

     Zostanie otwarte doświadczalne wystąpienie programu Visual Studio z zainstalowaną niestandardową stroną startową, ale nie została wybrana.

2. W eksperymentalnym wystąpieniu programu Visual Studio Otwórz stronę **Narzędzia/Options/środowisko** .

3. Wybierz pozycję **Uruchamianie**. Na liście **Dostosuj stronę początkową** wybierz plik *XAML* , a następnie kliknij przycisk **OK**.

4. W menu **Widok** kliknij pozycję **Strona początkowa**.

5. Kliknij kartę **Bing** .

     Powinna zostać wyświetlona strona sieci Web Bing.

6. Kliknij kartę Moje **przyciski** .

     Powinien zostać wyświetlony przycisk "mój **projekt** ", który otwiera okno dialogowe **Nowy projekt** .

7. Zamknij wystąpienie eksperymentalne.

Aby zastosować niestandardową stronę początkową, w obszarze **Narzędzia**  >  **Opcje**  >  **środowisko**wybierz pozycję **Uruchamianie**. Na liście **Dostosuj stronę początkową** wybierz plik *XAML* , a następnie kliknij przycisk **OK**.

## <a name="next-steps"></a>Następne kroki

Strona startowa programu Visual Studio zawiera teraz kartę wyświetlającą kartę przeglądarki sieci Web i kartę z przyciskiem. Można utworzyć niestandardowe strony startowe, które mają inne funkcje przy użyciu modelu *związanego z kodem* do dodania pliku Custom. dll, jak pokazano w temacie [Dodawanie kontrolki użytkownika do strony Start](../extensibility/adding-user-control-to-the-start-page.md). Niestandardowe strony startowe można udostępniać innym użytkownikom, publikując plik. vsix w witrynie sieci Web [Visual Studio Marketplace](https://marketplace.visualstudio.com/) lub do innej witryny sieci Web lub udziału sieciowego. Aby uzyskać więcej informacji, zobacz [wdrażanie niestandardowych stron początkowych](../extensibility/deploying-custom-start-pages.md).

## <a name="see-also"></a>Zobacz też

- [Dostosuj stronę początkową](../ide/customizing-the-start-page-for-visual-studio.md)
- [Formanty kontenera WPF](https://msdn.microsoft.com/library/a0177167-d7db-4205-9607-8ae316952566)
