---
title: 'Przewodnik: Tworzenie składnika Web Part dla SharePoint | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], developing
- Web Parts [SharePoint development in Visual Studio], creating
- Web Parts [SharePoint development in Visual Studio], designing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 622dfafbe16efee1e953fbc42bfa3b94cfa3cc58
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62965274"
---
# <a name="walkthrough-create-a-web-part-for-sharepoint"></a>Przewodnik: Tworzenie składnika web part programu SharePoint

Części sieci Web umożliwiają użytkownikom bezpośrednio modyfikować zawartość, wygląd i zachowanie stron w witrynie programu SharePoint za pomocą przeglądarki. W tym instruktażu pokazano, jak utworzyć składnik Web Part za pomocą **składnika Web Part** szablonu elementu w programie Visual Studio 2010.

Składnik Web Part wyświetla pracowników w siatce danych. Użytkownik określa lokalizację pliku, który zawiera dane pracowników. Użytkownika można również filtrować siatki danych, tak aby pracownicy, którzy są menedżerowie są wyświetlane na liście tylko.

W instruktażu przedstawiono następujące zagadnienia:

- Tworzenie składnika Web Part za pomocą programu Visual Studio **składnika Web Part** szablon elementu.

- Tworzenie właściwości, które można ustawić przez użytkownika składnika Web Part. Ta właściwość określa lokalizację pliku danych pracownika.

- Renderowanie zawartości składnika Web Part, dodając formanty do składnika Web Part steruje kolekcji.

- Tworzenie nowego elementu menu, nazywane *zlecenie,* wyświetlany w menu zleceń renderowanych składnika Web Part. Czasowniki umożliwić użytkownikowi modyfikowanie danych, który pojawia się w składniku Web Part.

- Testowanie części sieci Web w programie SharePoint.

    > [!NOTE]
    > Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Wymagania wstępne

- Obsługiwane wersje systemu Microsoft Windows i programu SharePoint.

- Program Visual Studio 2017 lub usługi Azure DevOps.

## <a name="create-an-empty-sharepoint-project"></a>Utwórz pusty projekt programu SharePoint

Najpierw utwórz projekt programu SharePoint puste. Później dodasz składnika Web Part do projektu przy użyciu **składnika Web Part** szablon elementu.

1. Rozpocznij [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] przy użyciu **Uruchom jako Administrator** opcji.

2. Na pasku mężczyzn wybierz **pliku** > **New** > **projektu**.

3. W **nowy projekt** okna dialogowego rozwiń **SharePoint** węzła dla języka, który chcesz użyć, a następnie wybierz **2010** węzła.

4. W **szablony** okienku wybierz **projekt programu SharePoint 2010**, a następnie wybierz **OK** przycisku.

     **Kreator ustawień niestandardowych SharePoint** pojawia się. Ten kreator umożliwia wybór lokacji, który będzie używany do debugowania projektu i poziomu zaufania rozwiązania.

5. Wybierz **Wdróż jako rozwiązanie farmy** przycisk opcji, a następnie wybierz **Zakończ** przycisk, aby zaakceptować domyślne lokalnej witryny programu SharePoint.

## <a name="add-a-web-part-to-the-project"></a>Dodawanie składnika web part do projektu

Dodaj **składnika Web Part** do projektu. **Składnika Web Part** elementu dodaje plik kodu składnika Web Part. Później dodasz kod do pliku kodu składnika Web Part do renderowania zawartości składnika Web Part.

1. Na pasku menu wybierz **projektu** > **Dodaj nowy element**.

2. W **Dodaj nowy element** okno dialogowe, **zainstalowane szablony** okienku rozwiń **SharePoint** węzła, a następnie wybierz **2010** węzła.

3. Na liście szablonów programu SharePoint, wybierz opcję **składnika Web Part** szablonu, a następnie wybierz **Dodaj** przycisku.

     **Składnika Web Part** element będzie wyświetlany w **Eksploratora rozwiązań**.

## <a name="rendering-content-in-the-web-part"></a>Renderowanie zawartości w składniku web part

Można określić, które kontrolki mają być wyświetlane w składniku Web Part, dodając je do kolekcji controls klasy składnika Web Part.

1. W **Eksploratora rozwiązań**, otwórz *WebPart1.vb* (w języku Visual Basic) lub *WebPart1.cs* (w języku C#).

     Plik kodu części sieci Web zostanie otwarty w edytorze kodu.

2. Dodaj następujące instrukcje na górze pliku kodu składnika Web Part.

     [!code-csharp[SP_WebPart#1](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#1)]
     [!code-vb[SP_WebPart#1](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#1)]

3. Dodaj następujący kod do `WebPart1` klasy. Ten kod deklaruje następujące pola:

   - Siatka danych do wyświetlenia pracowników w składniku Web Part.

   - Tekst wyświetlany w kontrolce, która jest używana do filtrowania siatki danych.

   - Etykiety, która wyświetla komunikat o błędzie, jeśli siatki danych nie jest w stanie wyświetlić dane.

   - Ciąg, który zawiera ścieżkę do pliku danych pracownika.

     [!code-csharp[SP_WebPart#2](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#2)]
     [!code-vb[SP_WebPart#2](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#2)]

4. Dodaj następujący kod do `WebPart1` klasy. Ten kod dodaje właściwość niestandardową o nazwie `DataFilePath` do składnika Web Part. Właściwość niestandardowa jest właściwością, która może być ustawiona przez użytkownika w programie SharePoint. Tej właściwości pobiera i Ustawia lokalizację pliku danych XML, która jest używana do zapełniania siatki danych.

     [!code-csharp[SP_WebPart#3](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#3)]
     [!code-vb[SP_WebPart#3](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#3)]

5. Zastąp `CreateChildControls` metoda następującym kodem. Kod będzie wykonywał następujące zadania:

   - Dodaje siatki danych i etykiety, która została zadeklarowana w poprzednim kroku.

   - Wiąże siatki danych do pliku XML, który zawiera dane pracowników.

     [!code-csharp[SP_WebPart#4](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#4)]
     [!code-vb[SP_WebPart#4](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#4)]

6. Dodaj następującą metodę do `WebPart1` klasy. Kod będzie wykonywał następujące zadania:

   - Tworzy zlecenia, który pojawia się w menu zleceń składnika Web Part renderowanych składnika Web Part.

   - Obsługuje zdarzenie, które jest wywoływane, gdy użytkownik wybierze czasownika w menu zleceń. Ten kod filtry listę pracowników, który pojawia się w siatce danych.

     [!code-csharp[SP_WebPart#5](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#5)]
     [!code-vb[SP_WebPart#5](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#5)]

## <a name="test-the-web-part"></a>Testowanie części sieci web

Kiedy uruchamiasz projekt, otwiera się witryna SharePoint. Składnik Web Part jest automatycznie dodawane do galerii Web Part w programie SharePoint. Składnik Web Part można dodać do dowolnej strony składnika Web Part.

1. Wklej następujący kod XML do pliku Notatnika. Ten plik XML zawiera przykładowe dane, która będzie wyświetlana w składniku Web Part.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
        <employees xmlns="http://schemas.microsoft.com/vsto/samples">
           <employee>
               <name>David Hamilton</name>
               <hireDate>2001-05-11</hireDate>
               <title>Sales Associate</title>
           </employee>
           <employee>
               <name>Karina Leal</name>
               <hireDate>1999-04-01</hireDate>
               <title>Manager</title>
           </employee>
           <employee>
               <name>Nancy Davolio</name>
               <hireDate>1992-05-01</hireDate>
               <title>Sales Associate</title>
           </employee>
           <employee>
               <name>Steven Buchanan</name>
               <hireDate>1955-03-04</hireDate>
               <title>Manager</title>
           </employee>
           <employee>
               <name>Suyama Michael</name>
               <hireDate>1963-07-02</hireDate>
               <title>Sales Associate</title>
           </employee>
        </employees>
    ```

2. W programie Notatnik, na pasku menu wybierz **pliku** > **Zapisz jako**.

3. W **Zapisz jako** dialogowym **Zapisz jako typ** wybierz **wszystkie pliki**.

4. W **nazwy pliku** wprowadź **data.xml**.

5. Wybierz dowolny folder przy użyciu **Przeglądaj foldery** przycisk, a następnie wybierz **Zapisz** przycisku.

6. W programie Visual Studio, wybierz **F5** klucza.

     Otwiera się witryna SharePoint.

7. Na **Akcje witryny** menu, wybierz **więcej opcji**.

8. W **Utwórz** wybierz **strona składników Web Part** typu, a następnie wybierz **Utwórz** przycisku.

9. W **nowej strony składników Web Part** strony, nazwij stronę **SampleWebPartPage.aspx**, a następnie wybierz **Utwórz** przycisku.

     Zostanie wyświetlona strona składników Web Part.

10. Wybierz wszystkie strefy na stronę składników Web Part.

11. W górnej części strony wybierz **Wstaw** kartę, a następnie wybierz **składnika Web Part** przycisku.

12. W **kategorie** okienku wybierz **niestandardowe** folderu, wybierz **WebPart1** składnika Web Part, a następnie wybierz **Dodaj** przycisku.

     Składnik Web Part jest wyświetlany na stronie.

## <a name="test-the-custom-property"></a>Testowanie właściwości niestandardowej

Do zapełniania siatki danych, który pojawia się w składniku Web Part, określ ścieżkę pliku XML, który zawiera dane dotyczące każdego pracownika.

1. Wybierz strzałkę, która pojawia się po prawej stronie składnika Web Part, a następnie wybierz **Edytuj składnik Web Part** z wyświetlonego menu.

     W prawej części strony pojawi się okienko, który zawiera właściwości składnika Web Part.

2. W okienku rozwiń **różne** węzła, wprowadź ścieżkę do pliku XML, który został utworzony wcześniej, wybierz polecenie **Zastosuj** przycisk, a następnie wybierz **OK** przycisku.

     Sprawdź, czy lista pracowników znajduje się w składniku Web Part.

## <a name="test-the-web-part-verb"></a>Testowanie zlecenia części sieci web

Pokazywanie i ukrywanie pracownicy, którzy nie są menedżerów, klikając pozycję elementu, który jest wyświetlany w menu zleceń składnika Web Part.

1. Wybierz strzałkę, która pojawia się po prawej stronie składnika Web Part, a następnie wybierz **Pokaż tylko menedżerowie** z wyświetlonego menu.

     Tylko pracownicy, którzy są menedżerowie pojawiają się w składniku Web Part.

2. Wybierz strzałkę ponownie, a następnie wybierz **Pokaż wszyscy pracownicy** z wyświetlonego menu.

     Wszyscy pracownicy są wyświetlane w składniku Web Part.

## <a name="see-also"></a>Zobacz także

[Tworzenie składników web Part programu SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
[jak: Tworzenie składnika web part programu SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)
[jak: Tworzenie części sieciowej SharePoint za pomocą projektanta](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)
[instruktażu: Tworzenie składnika web part programu SharePoint przy użyciu narzędzia Projektant](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)
