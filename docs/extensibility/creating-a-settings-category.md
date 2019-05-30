---
title: Tworzenie kategorii ustawień | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profile settings, creating categories
ms.assetid: 97c88693-05ff-499e-8c43-352ee073dcb7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 02ef202436e12ae075c41f507577bacaa968c60b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341582"
---
# <a name="create-a-settings-category"></a>Tworzenie kategorii ustawień

W tym przewodniku utworzysz kategorii ustawień programu Visual Studio i używać go do wartości, aby zapisać i przywrócić wartości z pliku ustawień. Kategoria ustawień jest grupą powiązanych właściwości, które są wyświetlane jako "punkt ustawień niestandardowych;" oznacza to, że pole wyboru w **importowanie i eksportowanie ustawień** kreatora. (Można znaleźć na **narzędzia** menu.) Ustawienia są zapisywane lub przywrócone jako kategorii, a poszczególne ustawienia nie są wyświetlane w kreatorze. Aby uzyskać więcej informacji, zobacz [ustawienia środowiska](../ide/environment-settings.md).

Tworzenie kategorii ustawień przez wywodzić ją z <xref:Microsoft.VisualStudio.Shell.DialogPage> klasy.

Aby uruchomić ten Instruktaż, najpierw musisz zakończyć w pierwszej sekcji [utworzyć stronę opcji](../extensibility/creating-an-options-page.md). Wynikowy siatki właściwości opcje pozwala sprawdzić i zmienić właściwości w kategorii. Po zapisaniu kategorii właściwości w pliku ustawień, zapoznaj się z plikiem, aby zobaczyć, jak są przechowywane wartości właściwości.

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, możesz nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest dołączony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [instalacji programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-settings-category"></a>Tworzenie kategorii ustawień
 W tej sekcji umożliwia punktu niestandardowych ustawień zapisywanie i przywracanie wartości kategorii ustawień.

### <a name="to-create-a-settings-category"></a>Aby utworzyć kategorii ustawień

1. Wykonaj [utworzyć stronę opcji](../extensibility/creating-an-options-page.md).

2. Otwórz *VSPackage.resx* pliku i Dodaj te zasoby trzy parametry:

    |Nazwa|Wartość|
    |----------|-----------|
    |106|Moje kategorii|
    |107|Moje ustawienia|
    |108|OptionInteger i OptionFloat|

     Spowoduje to utworzenie zasobów tej nazwy kategorii "Moje Category", "Moje ustawienia obiektu" i opis kategorii "OptionInteger i OptionFloat".

    > [!NOTE]
    > Z tych trzech nazwę kategorii nie ma **Import i eksport ustawień** kreatora.

3. W *MyToolsOptionsPackage.cs*, Dodaj `float` właściwość o nazwie `OptionFloat` do `OptionPageGrid` klasy, jak pokazano w poniższym przykładzie.

    ```csharp
    public class OptionPageGrid : DialogPage
    {
        private int optionInt = 256;
        private float optionFloat = 3.14F;

        [Category("My Options")]
        [DisplayName("My Integer option")]
        [Description("My integer option")]
        public int OptionInteger
        {
            get { return optionInt; }
            set { optionInt = value; }
        }
        [Category("My Options")]
        [DisplayName("My Float option")]
        [Description("My float option")]
        public float OptionFloat
        {
            get { return optionFloat; }
            set { optionFloat = value; }
        }
    }
    ```

    > [!NOTE]
    > `OptionPageGrid` Kategorii o nazwie "My Category" teraz składa się z dwóch właściwości `OptionInteger` i `OptionFloat`.

4. Dodaj <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> do `MyToolsOptionsPackage` klasy i nadać mu CategoryName "Moje Category", nadaj ObjectName "Moje ustawienia" i ustawić isToolsOptionPage na wartość true. Ustaw categoryResourceID objectNameResourceID i DescriptionResourceID do odpowiedniego zasobu ciągu, który identyfikatorów utworzonych wcześniej.

    ```csharp
    [ProvideProfileAttribute(typeof(OptionPageGrid),
        "My Category", "My Settings", 106, 107, isToolsOptionPage:true, DescriptionResourceID = 108)]
    ```

5. Skompiluj projekt, a następnie rozpocząć debugowanie. W doświadczalnym wystąpieniu powinien zostać wyświetlony, **Moja strona siatki** ma teraz wartości typu Liczba całkowita i zmiennoprzecinkowa.

## <a name="examine-the-settings-file"></a>Zapoznaj się z plikiem ustawień
 W tej sekcji możesz wyeksportować do pliku ustawień właściwości wartości kategorii. Zapoznaj się z plikiem, a następnie zaimportować wartości z powrotem do kategorii właściwości.

1. Rozpocznij projekt w trybie debugowania, naciskając klawisz **F5**. Spowoduje to uruchomienie wystąpienie eksperymentalne.

2. Otwórz **narzędzia** > **opcje** okna dialogowego.

3. W widoku drzewa w lewym okienku rozwiń **Moje kategorii** a następnie kliknij przycisk **Moja strona siatki**.

4. Zmień wartość właściwości **OptionFloat** do 3.1416 i **OptionInteger** do 12. Kliknij przycisk **OK**.

5. Na **narzędzia** menu, kliknij przycisk **Import i eksport ustawień**.

     **Import i eksport ustawień** pojawi się Kreator.

6. Upewnij się, że **Eksportuj wybrane ustawienia środowiska** jest zaznaczone, a następnie kliknij przycisk **dalej**.

     **Wybierz ustawienia do eksportowania** zostanie wyświetlona strona.

7. Kliknij przycisk **Moje ustawienia**.

     **Opis** zmieni się na **OptionInteger i OptionFloat**.

8. Upewnij się, że **Moje ustawienia** jest tylko kategorię, która jest zaznaczone, a następnie kliknij przycisk **dalej**.

     **Nazwę pliku ustawień** zostanie wyświetlona strona.

9. Nadaj nowemu plikowi ustawień *MySettings.vssettings* i zapisz go w odpowiednim katalogu. Kliknij przycisk **Zakończ**.

     **Eksportowanie ukończone** strony zgłasza, że Twoje ustawienia zostały pomyślnie wyeksportowane.

10. Na **pliku** menu wskaż **Otwórz**, a następnie kliknij przycisk **pliku**. Znajdź *MySettings.vssettings* i otwórz go.

     Możesz znaleźć kategorii właściwości, który został wyeksportowany w poniższej sekcji pliku (swoje identyfikatory GUID będą się różnić).

    ```
    <Category name="My Category_My Settings"
          Category="{4802bc3e-3d9d-4591-8201-23d1a05216a6}"
          Package="{6bb6942e-014c-489e-a612-a935680f703d}"
          RegisteredName="My Category_My Settings">
          PackageName="MyToolsOptionsPackage">
       <PropertyValue name="OptionFloat">3.1416</PropertyValue>
       <PropertyValue name="OptionInteger">12</PropertyValue>
    </Category>
    ```

     Należy zauważyć, że nazwa kategorii pełną został utworzony przez dodanie znaku podkreślenia, aby nazwa kategorii, a następnie według nazwy obiektu. OptionFloat i OptionInteger pojawiają się w danej kategorii, wraz z ich wartości eksportowanych.

11. Zamknij plik ustawień, nie zmieniając go.

12. Na **narzędzia** menu, kliknij przycisk **opcje**, rozwiń węzeł **Moje kategorii**, kliknij przycisk **Moja strona siatki** , a następnie zmień wartość  **OptionFloat** 1.0 i **OptionInteger** 1. Kliknij przycisk **OK**.

13. Na **narzędzia** menu, kliknij przycisk **Import i eksport ustawień**, wybierz opcję **Importuj ustawienia wybranego środowiska**, a następnie kliknij przycisk **dalej**.

     **Zapisać bieżące ustawienia** zostanie wyświetlona strona.

14. Wybierz **nie, tylko zaimportuj nowe ustawienia** a następnie kliknij przycisk **dalej**.

     **Wybierz kolekcję ustawień do zaimportowania** zostanie wyświetlona strona.

15. Wybierz *MySettings.vssettings* w pliku **Moje ustawienia** węzła widoku drzewa. Jeśli plik nie zostanie wyświetlony w widoku drzewa, kliknij przycisk **Przeglądaj** i poszukaj ich. Kliknij przycisk **Dalej**.

     **Wybierz ustawienia do importowania** pojawi się okno dialogowe.

16. Upewnij się, że **Moje ustawienia** jest zaznaczone, a następnie kliknij przycisk **Zakończ**. Gdy **pełny Import** zostanie wyświetlona strona, kliknij przycisk **Zamknij**.

17. Na **narzędzia** menu, kliknij przycisk **opcje**, rozwiń węzeł **Moje kategorii**, kliknij przycisk **Moja strona siatki** i sprawdź, czy wartości właściwości w kategorii zostały przywrócone.