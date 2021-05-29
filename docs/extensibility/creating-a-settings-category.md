---
title: Tworzenie ustawienia kategorii | Microsoft Docs
description: Dowiedz się, jak utworzyć kategorię ustawień Visual Studio i używać jej do zapisywania i przywracania wartości z pliku ustawień.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- profile settings, creating categories
ms.assetid: 97c88693-05ff-499e-8c43-352ee073dcb7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fe46ea835a119978fd3decd26949db3d59944e5e
ms.sourcegitcommit: 63cb90e8cea112aa2ce8741101b309dbc709e393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2021
ms.locfileid: "110687617"
---
# <a name="create-a-settings-category"></a>Tworzenie kategorii ustawień

W tym przewodniku utworzysz kategorię ustawień Visual Studio i użyjemy jej do zapisywania wartości i przywracania wartości z pliku ustawień. Kategoria ustawień to grupa powiązanych właściwości, które są wyświetlane jako "niestandardowy punkt ustawień"; oznacza to, że jako pole wyboru w **Kreatorze importowania i eksportowania** ustawień. (Można go znaleźć w **menu** Narzędzia). Ustawienia są zapisywane lub przywracane jako kategoria, a poszczególne ustawienia nie są wyświetlane w kreatorze. Aby uzyskać więcej informacji, zobacz [Ustawienia środowiska](../ide/environment-settings.md).

Kategorię ustawień tworzy się, wyprowadzając ją z <xref:Microsoft.VisualStudio.Shell.DialogPage> klasy .

Aby rozpocząć ten przewodnik, należy najpierw ukończyć pierwszą sekcję strony [Tworzenie opcji.](../extensibility/creating-an-options-page.md) Wynikowa siatka właściwości Opcje umożliwia badanie i zmienianie właściwości w kategorii. Po zapisaniu kategorii właściwości w pliku ustawień należy zbadać plik, aby zobaczyć, jak są przechowywane wartości właściwości.

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od Visual Studio 2015 r., zestaw SDK usługi Visual Studio nie jest instalowany z Centrum pobierania. Jest ona dołączona jako opcjonalna funkcja w Visual Studio konfiguracji. Zestaw VS SDK można również zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-settings-category"></a>Tworzenie kategorii ustawień
 W tej sekcji użyjemy punktu ustawień niestandardowych, aby zapisać i przywrócić wartości kategorii ustawień.

### <a name="to-create-a-settings-category"></a>Aby utworzyć kategorię ustawień

1. Ukończ stronę [Tworzenie opcji.](../extensibility/creating-an-options-page.md)

2. Otwórz plik *VSPackage.resx* i dodaj następujące trzy zasoby ciągu:

    |Nazwa|Wartość|
    |----------|-----------|
    |106|Moja kategoria|
    |107|Moje ustawienia|
    |108|OptionInteger i OptionFloat|

     Spowoduje to utworzenie zasobów, które będą nazywać się kategorią "Moja kategoria", obiektem "Moje ustawienia" i opisem kategorii "OptionInteger and OptionFloat".

    > [!NOTE]
    > Z tych trzech tylko nazwa kategorii nie jest wyświetlana w **kreatorze importowania i eksportowania** ustawień.

3. W *myToolsOptionsPackage.cs* dodaj właściwość o `float` nazwie do klasy , jak `OptionFloat` `OptionPageGrid` pokazano w poniższym przykładzie.

    ```csharp
    public class OptionPageGrid : DialogPage
    {
        private int optionInt = 256;
        private float optionFloat = 3.14F;

        [Category("My Options")]
        [DisplayName("My Integer option")]
        [Description("My integer option")]
        public int OptionInteger
        {
            get { return optionInt; }
            set { optionInt = value; }
        }
        [Category("My Options")]
        [DisplayName("My Float option")]
        [Description("My float option")]
        public float OptionFloat
        {
            get { return optionFloat; }
            set { optionFloat = value; }
        }
    }
    ```

    > [!NOTE]
    > Kategoria `OptionPageGrid` o nazwie "Moja kategoria" składa się teraz z dwóch właściwości: `OptionInteger` i `OptionFloat` .

4. Dodaj do klasy wartość i nadaj jej nazwę CategoryName "Moja kategoria", nadaj jej nazwę ObjectName "My Settings" i ustaw dla właściwości <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> `MyToolsOptionsPackage` isToolsOptionPage wartość true. Ustaw wartości categoryResourceID, objectNameResourceID i DescriptionResourceID na odpowiednie identyfikatory zasobów ciągu utworzone wcześniej.

    ```csharp
    [ProvideProfileAttribute(typeof(OptionPageGrid),
        "My Category", "My Settings", 106, 107, isToolsOptionPage:true, DescriptionResourceID = 108)]
    ```

5. Skompilowanie projektu i rozpoczęcie debugowania. W wystąpieniu eksperymentalnym powinna być widać, że moja **strona siatki** ma teraz zarówno wartości całkowite, jak i zmiennoprzecinkowa.

## <a name="examine-the-settings-file"></a>Badanie pliku ustawień
 W tej sekcji wartości kategorii właściwości są eksportowane do pliku ustawień. Przeanalizujesz plik, a następnie zaimportujesz wartości z powrotem do kategorii właściwości.

1. Uruchom projekt w trybie debugowania, naciskając **klawisz F5**. To uruchamia wystąpienie eksperymentalne.

2. Otwórz okno  >  **dialogowe Opcje** narzędzi.

3. W widoku drzewa w okienku po lewej stronie rozwiń **pozycję Moja kategoria,** a następnie kliknij pozycję **Moja strona siatki**.

4. Zmień wartość **OptionFloat** na 3,1416 i **OptionInteger** na 12. Kliknij przycisk **OK**.

5. W menu **Narzędzia** kliknij pozycję **Importuj i eksportuj ustawienia.**

     Zostanie **wyświetlony kreator Importowanie i eksportowanie** ustawień.

6. Upewnij się, **że zaznaczono opcję Eksportuj wybrane** ustawienia środowiska, a następnie kliknij przycisk **Dalej.**

     Zostanie **wyświetlona strona Wybierz ustawienia do** wyeksportowania.

7. Kliknij **pozycję Moje ustawienia.**

     W **polu Opis** zostaną wprowadzone opcje **OptionInteger i OptionFloat.**

8. Upewnij się, **że wybrano** tylko wybraną kategorię Moje ustawienia, a następnie kliknij przycisk **Dalej.**

     Zostanie **wyświetlona strona Nazwa pliku** ustawień.

9. Nadaj nowemu plikowi *ustawień nazwę MySettings.vssettings* i zapisz go w odpowiednim katalogu. Kliknij przycisk **Finish** (Zakończ).

   Plik `.vssettings` jest plikiem Visual Studio ustawień sieciowych. Schemat pliku jest otwarty. Najczęściej schemat jest zgodny ze strukturą XML, w której każda kategoria jest tagiem, który sam może zawierać tagi podkategorii. Tagi podkategorie mogą zawierać tagi wartości właściwości. Chociaż większość pakietów używa wspólnej struktury, każdy pakiet w Visual Studio może współtwolić dowolny kod XML do pliku przy użyciu wybieranych schematów.

   Na **stronie Eksportuj** ukończono jest raportowany, że ustawienia zostały pomyślnie wyeksportowane.

10. W menu **Plik** wskaż polecenie **Otwórz,** a następnie kliknij pozycję **Plik.** Znajdź *mySettings.vssettings* i otwórz go.

     Kategorię właściwości wyeksportowaną w poniższej sekcji pliku można znaleźć (identyfikatory GUID będą się różnić).

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

     Zwróć uwagę, że pełna nazwa kategorii jest postać przez dodanie podkreślenia do nazwy kategorii, po której następuje nazwa obiektu. Opcje OptionFloat i OptionInteger są wyświetlane w kategorii wraz z ich wyeksportowane wartości.

11. Zamknij plik ustawień bez jego zmiany.

12. W menu **Narzędzia** kliknij pozycję **Opcje,** rozwiń pozycję Moja **kategoria,** kliknij pozycję **Moja** strona siatki, a następnie zmień wartość **opcjiFloat** na 1.0, a **opcjęInteger** na 1. Kliknij przycisk **OK**.

13. W menu **Narzędzia** kliknij pozycję **Importuj i eksportuj ustawienia,** wybierz **pozycję Importuj wybrane ustawienia środowiska,** a następnie kliknij przycisk **Dalej.**

     Zostanie **wyświetlona strona Zapisz bieżące** ustawienia.

14. Wybierz **pozycję Nie, po prostu zaimportuj nowe ustawienia,** a następnie kliknij przycisk **Dalej.**

     Zostanie **wyświetlona strona Wybierz kolekcję ustawień do zaimportowania.**

15. Wybierz plik *MySettings.vssettings* w węźle **Moje** ustawienia w widoku drzewa. Jeśli plik nie jest wyświetlany w widoku drzewa, kliknij przycisk **Przeglądaj** i znajdź go. Kliknij przycisk **Dalej**.

     Zostanie **wyświetlone okno dialogowe Wybieranie ustawień do** zaimportowania.

16. Upewnij się, **że wybrano pozycję Moje** ustawienia, a następnie kliknij przycisk **Zakończ.** Gdy zostanie **wyświetlona strona Import Complete (Importuj** zakończone), kliknij pozycję **Close (Zamknij).**

17. W menu **Narzędzia** kliknij pozycję **Opcje,** rozwiń pozycję **Moja kategoria,** kliknij pozycję **Moja** strona siatki i sprawdź, czy wartości kategorii właściwości zostały przywrócone.
