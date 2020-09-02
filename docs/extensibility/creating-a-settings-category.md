---
title: Tworzenie kategorii ustawień | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- profile settings, creating categories
ms.assetid: 97c88693-05ff-499e-8c43-352ee073dcb7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03d50ca998efa034b1d4392c1fb7cecb8de8ed06
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85904022"
---
# <a name="create-a-settings-category"></a>Utwórz kategorię ustawień

W tym instruktażu utworzysz kategorię ustawień programu Visual Studio i użyjesz jej do zapisania wartości i przywrócenia wartości z pliku ustawień. Kategoria ustawień jest grupą powiązanych właściwości, które pojawiają się jako "punkt ustawień niestandardowych"; oznacza to, że jest to pole wyboru w kreatorze **importowania i eksportowania ustawień** . (Można je znaleźć w menu **Narzędzia** ). Ustawienia są zapisywane lub przywracane jako kategoria, a poszczególne ustawienia nie są wyświetlane w kreatorze. Aby uzyskać więcej informacji, zobacz [Ustawienia środowiska](../ide/environment-settings.md).

Można utworzyć kategorię ustawień, usuwając ją z <xref:Microsoft.VisualStudio.Shell.DialogPage> klasy.

Aby rozpocząć ten przewodnik, należy najpierw wykonać pierwszą sekcję [tworzenia strony opcji](../extensibility/creating-an-options-page.md). Siatka właściwości opcje wyników umożliwia badanie i zmiana właściwości w kategorii. Po zapisaniu kategorii właściwości w pliku ustawień należy sprawdzić plik, aby zobaczyć, w jaki sposób są przechowywane wartości właściwości.

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, nie należy instalować zestawu Visual Studio SDK z centrum pobierania. Jest ona dostępna jako opcjonalna funkcja w Instalatorze programu Visual Studio. Zestaw VS SDK można także zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-settings-category"></a>Utwórz kategorię ustawień
 W tej sekcji używany jest punkt ustawień niestandardowych do zapisywania i przywracania wartości kategorii ustawień.

### <a name="to-create-a-settings-category"></a>Aby utworzyć kategorię ustawień

1. Wypełnij [stronę tworzenie opcji](../extensibility/creating-an-options-page.md).

2. Otwórz plik *pakietu VSPackage. resx* i Dodaj następujące trzy zasoby ciągu:

    |Nazwa|Wartość|
    |----------|-----------|
    |106|Moja Kategoria|
    |107|Moje ustawienia|
    |108|OptionInteger i OptionFloat|

     Spowoduje to utworzenie zasobów należących do kategorii "My Category", obiektu "My Settings" i opisu kategorii "OptionInteger and OptionFloat".

    > [!NOTE]
    > Z tych trzech, tylko nazwa kategorii nie jest wyświetlana w kreatorze **importowania i eksportowania ustawień** .

3. W *MyToolsOptionsPackage.cs*Dodaj `float` Właściwość o nazwie `OptionFloat` do `OptionPageGrid` klasy, jak pokazano w poniższym przykładzie.

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
    > `OptionPageGrid`Kategoria o nazwie "My Category" zawiera teraz dwie właściwości `OptionInteger` i `OptionFloat` .

4. Dodaj <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> do `MyToolsOptionsPackage` klasy i nadaj jej CategoryName "My Category", nadaj jej obiektowi ObjectName "My Settings" i ustaw isToolsOptionPage na true. Ustaw wartości categoryResourceID, objectNameResourceID i DescriptionResourceID na odpowiednie identyfikatory zasobów ciągu utworzone wcześniej.

    ```csharp
    [ProvideProfileAttribute(typeof(OptionPageGrid),
        "My Category", "My Settings", 106, 107, isToolsOptionPage:true, DescriptionResourceID = 108)]
    ```

5. Skompiluj projekt i Rozpocznij debugowanie. W eksperymentalnym wystąpieniu powinno być widoczne, że **Strona Moje siatki** zawiera teraz wartości całkowite i zmiennoprzecinkowe.

## <a name="examine-the-settings-file"></a>Sprawdzanie pliku ustawień
 W tej sekcji można wyeksportować wartości kategorii właściwości do pliku ustawień. Należy przeanalizować plik, a następnie zaimportować wartości z powrotem do kategorii właściwości.

1. Uruchom projekt w trybie debugowania, naciskając klawisz **F5**. Spowoduje to uruchomienie eksperymentalnego wystąpienia.

2. Otwórz **Tools**  >  okno dialogowe**Opcje** narzędzi.

3. W widoku drzewa w lewym okienku rozwiń węzeł **moja Kategoria** , a następnie kliknij pozycję **moja strona siatki**.

4. Zmień wartość **OptionFloat** na 3,1416 i **OptionInteger** na 12. Kliknij przycisk **OK**.

5. W menu **Narzędzia** kliknij pozycję **Importuj i Eksportuj ustawienia**.

     Zostanie wyświetlony Kreator **importowania i eksportowania ustawień** .

6. Upewnij się, że wybrano opcję **Eksportuj wybrane ustawienia środowiska** , a następnie kliknij przycisk **dalej**.

     Zostanie wyświetlona strona **Wybierz ustawienia do eksportowania** .

7. Kliknij pozycję **Moje ustawienia**.

     **Opis** zmieni się na **OptionInteger i OptionFloat**.

8. Upewnij się, że **Moje ustawienia** są jedyną wybraną kategorią, a następnie kliknij przycisk **dalej**.

     Zostanie wyświetlona strona **Nazwij plik ustawień** .

9. Nadaj nazwę nowemu plikowi ustawień *. vssettings* i Zapisz ją w odpowiednim katalogu. Kliknij przycisk **Zakończ**.

     Na stronie **Eksportowanie zakończą** się raporty, że Twoje ustawienia zostały pomyślnie wyeksportowane.

10. W menu **plik** wskaż polecenie **Otwórz**, a następnie kliknij pozycję **plik**. Znajdź element *websettings. vssettings* i otwórz go.

     Możesz znaleźć kategorię właściwości wyeksportowaną w poniższej sekcji pliku (identyfikatory GUID różnią się).

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

     Należy zauważyć, że pełna nazwa kategorii jest tworzona przez dodanie podkreślenia do nazwy kategorii, po której następuje nazwa obiektu. OptionFloat i OptionInteger są wyświetlane w kategorii wraz z wyeksportowanymi wartościami.

11. Zamknij plik ustawień bez zmiany.

12. W menu **Narzędzia** kliknij **Opcje**, rozwiń **moją kategorię**, kliknij pozycję **moja siatka** , a następnie zmień wartość **OptionFloat** na 1,0 i **OptionInteger** na 1. Kliknij przycisk **OK**.

13. W menu **Narzędzia** kliknij pozycję **Importuj i Eksportuj ustawienia**, wybierz opcję **Importuj wybrane ustawienia środowiska**, a następnie kliknij przycisk **dalej**.

     Zostanie wyświetlona strona **Zapisywanie bieżących ustawień** .

14. Wybierz pozycję **nie, po prostu zaimportuj nowe ustawienia** , a następnie kliknij przycisk **dalej**.

     Zostanie wyświetlona strona **Wybierz kolekcję ustawień do zaimportowania** .

15. Wybierz plik my *Settings. vssettings* w węźle **Moje ustawienia** w widoku drzewa. Jeśli plik nie jest wyświetlany w widoku drzewa, kliknij przycisk **Przeglądaj** i Znajdź go. Kliknij przycisk **Dalej**.

     Zostanie wyświetlone okno dialogowe **Wybieranie ustawień do zaimportowania** .

16. Upewnij się, że **Moje ustawienia** są zaznaczone, a następnie kliknij przycisk **Zakończ**. Gdy zostanie wyświetlona strona **Zakończono Importowanie** , kliknij przycisk **Zamknij**.

17. W menu **Narzędzia** kliknij przycisk **Opcje**, rozwiń **moją kategorię**, kliknij przycisk **moja strona siatki** i sprawdź, czy przywrócono wartości kategorii właściwości.
