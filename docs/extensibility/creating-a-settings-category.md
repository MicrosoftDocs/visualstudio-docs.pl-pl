---
title: Tworzenie kategorii ustawień | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profile settings, creating categories
ms.assetid: 97c88693-05ff-499e-8c43-352ee073dcb7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5f4b2fa9d82181d0eb899bf9680e8a9debd6c50b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739608"
---
# <a name="create-a-settings-category"></a>Tworzenie kategorii ustawień

W tym instruktażu należy utworzyć kategorię ustawień programu Visual Studio i używać jej do zapisywania wartości i przywracania wartości z pliku ustawień. Kategoria ustawień to grupa powiązanych właściwości, które są wyświetlane jako "punkt ustawień niestandardowych"; oznacza to, że jako pole wyboru w Kreatorze **Ustawienia importu i eksportu.** (Można go znaleźć w menu **Narzędzia).** Ustawienia są zapisywane lub przywracane jako kategoria, a poszczególne ustawienia nie są wyświetlane w kreatorze. Aby uzyskać więcej informacji, zobacz [Ustawienia środowiska](../ide/environment-settings.md).

Tworzenie kategorii ustawień przez wyprowadzanie go <xref:Microsoft.VisualStudio.Shell.DialogPage> z klasy.

Aby rozpocząć ten instruktaż, należy najpierw ukończyć pierwszą [sekcję strony Tworzenie opcji](../extensibility/creating-an-options-page.md). Wynikowa siatka właściwości Opcje umożliwia zbadanie i zmianę właściwości w kategorii. Po zapisaniu kategorii właściwości w pliku ustawień, należy sprawdzić plik, aby zobaczyć, jak wartości właściwości są przechowywane.

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, nie należy instalować visual studio SDK z centrum pobierania. Jest on dołączony jako opcjonalna funkcja w konfiguracji programu Visual Studio. Można również zainstalować vs SDK później. Aby uzyskać więcej informacji, zobacz [Instalowanie pakietu SDK programu Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-settings-category"></a>Tworzenie kategorii ustawień
 W tej sekcji służy niestandardowy punkt ustawień do zapisywania i przywracania wartości kategorii ustawień.

### <a name="to-create-a-settings-category"></a>Aby utworzyć kategorię ustawień

1. Ukończ [stronę Tworzenie opcji](../extensibility/creating-an-options-page.md).

2. Otwórz plik *VSPackage.resx* i dodaj te trzy zasoby ciągu:

    |Nazwa|Wartość|
    |----------|-----------|
    |106|Moja kategoria|
    |107|Moje ustawienia|
    |108|OptionInteger i OptionFloat|

     Spowoduje to utworzenie zasobów o nazwie "Moja kategoria", obiekt "Moje ustawienia" i opis kategorii "OptionInteger i OptionFloat".

    > [!NOTE]
    > Z tych trzech tylko nazwa kategorii nie jest wyświetlana w Kreatorze **Ustawienia importu i eksportu.**

3. W *MyToolsOptionsPackage.cs*, dodaj `float` właściwość `OptionFloat` o `OptionPageGrid` nazwie do klasy, jak pokazano w poniższym przykładzie.

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
    > Kategoria `OptionPageGrid` o nazwie "Moja kategoria" składa się teraz `OptionInteger` `OptionFloat`z dwóch właściwości i .

4. Dodaj <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> a `MyToolsOptionsPackage` do klasy i nadaj jej CategoryName "Moja kategoria", nadaj mu ObjectName "Moje ustawienia" i ustaw isToolsOptionPage na true. Ustaw identyfikator categoryResourceID, objectNameResourceID i DescriptionResourceID na odpowiednie identyfikatory zasobów ciągów utworzone wcześniej.

    ```csharp
    [ProvideProfileAttribute(typeof(OptionPageGrid),
        "My Category", "My Settings", 106, 107, isToolsOptionPage:true, DescriptionResourceID = 108)]
    ```

5. Skompiluj projekt i rozpocznij debugowanie. W eksperymentalnym wystąpieniu powinieneś zobaczyć, że **moja strona siatki** ma teraz wartości całkowite i zmiennoprzecinkowa.

## <a name="examine-the-settings-file"></a>Sprawdzanie pliku ustawień
 W tej sekcji można wyeksportować wartości kategorii właściwości do pliku ustawień. Sprawdź plik, a następnie zaimportować wartości z powrotem do kategorii właściwości.

1. Uruchom projekt w trybie debugowania, naciskając klawisz **F5**. Spowoduje to uruchomienie wystąpienia eksperymentalnego.

2. Otwórz okno dialogowe**Opcje** **narzędzi.** > 

3. W widoku drzewa w lewym okienku rozwiń węzeł **Moja kategoria,** a następnie kliknij pozycję **Moja strona siatki**.

4. Zmień wartość **OptionFloat** na 3.1416 i **OptionInteger** na 12. Kliknij przycisk **OK**.

5. W menu **Narzędzia** kliknij polecenie **Importuj i eksportuj ustawienia**.

     Zostanie wyświetlony Kreator **ustawień importu i eksportu.**

6. Upewnij się, że zaznaczona jest opcja **Eksportuj wybrane ustawienia środowiska,** a następnie kliknij przycisk **Dalej**.

     Zostanie wyświetlona strona **Wybierz ustawienia do wyeksportowania.**

7. Kliknij **pozycję Moje ustawienia**.

     **Opis** zmienia **optioninteger i optionfloat**.

8. Upewnij się, że **moje ustawienia** są jedyną kategorią, która jest zaznaczona, a następnie kliknij przycisk **Dalej**.

     Zostanie wyświetlona strona **Nazwa pliku ustawień.**

9. Nazwij nowy plik ustawień *MySettings.vssettings* i zapisz go w odpowiednim katalogu. Kliknij przycisk **Zakończ**.

     Strona **Eksportuj ukończone** informuje, że ustawienia zostały pomyślnie wyeksportowane.

10. W menu **Plik** wskaż polecenie **Otwórz**, a następnie kliknij polecenie **Plik**. Znajdź *mySettings.vssettings* i otwórz go.

     Kategorię właściwości wyeksportowałeś w poniższej sekcji pliku (identyfikatory GUID będą się różnić).

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

     Należy zauważyć, że pełna nazwa kategorii jest utworzona przez dodanie podkreślenia do nazwy kategorii, po której następuje nazwa obiektu. OptionFloat i OptionInteger pojawiają się w kategorii, wraz z ich wartości eksportowanych.

11. Zamknij plik ustawień bez jego zmiany.

12. W menu **Narzędzia** kliknij polecenie **Opcje**, rozwiń pozycję **Moja kategoria**, kliknij pozycję Moja **strona siatki,** a następnie zmień wartość **OptionFloat** na 1.0 i **OptionInteger** na 1. Kliknij przycisk **OK**.

13. W menu **Narzędzia** kliknij polecenie **Importuj i eksportuj ustawienia**, wybierz pozycję **Importuj wybrane ustawienia środowiska**, a następnie kliknij przycisk **Dalej**.

     Zostanie wyświetlona strona **Zapisz bieżące ustawienia.**

14. Wybierz **pozycję Nie, wystarczy zaimportować nowe ustawienia,** a następnie kliknąć przycisk **Dalej**.

     Zostanie wyświetlona strona **Wybierz kolekcję ustawień do zaimportowania.**

15. Wybierz plik *MySettings.vssettings* w węźle **Moje ustawienia** widoku drzewa. Jeśli plik nie jest wyświetlany w widoku drzewa, kliknij przycisk **Przeglądaj** i znajdź go. Kliknij przycisk **Dalej**.

     Zostanie wyświetlone okno dialogowe **Wybieranie ustawień do zaimportowania.**

16. Upewnij się, że zaznaczona jest opcja **Moje ustawienia,** a następnie kliknij przycisk **Zakończ**. Po **wyświetleniu** strony Importowanie zakończone kliknij przycisk **Zamknij**.

17. W menu **Narzędzia** kliknij polecenie **Opcje**, rozwiń węzeł **Moja kategoria**, kliknij pozycję Moja **strona siatki** i sprawdź, czy wartości kategorii właściwości zostały przywrócone.
