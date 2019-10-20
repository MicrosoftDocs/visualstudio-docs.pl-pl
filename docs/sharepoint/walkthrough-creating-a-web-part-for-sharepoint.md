---
title: 'Przewodnik: Tworzenie składnika Web Part dla programu SharePoint | Microsoft Docs'
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
ms.openlocfilehash: 3cbc4b9a2eecd6eb9853c515eb5358009c32843a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655912"
---
# <a name="walkthrough-create-a-web-part-for-sharepoint"></a>Przewodnik: Tworzenie składnika Web Part dla programu SharePoint

Składniki Web Part umożliwienie użytkownikom bezpośrednio modyfikować zawartość, wygląd i zachowanie stron witryny programu SharePoint za pomocą przeglądarki. W tym instruktażu przedstawiono sposób tworzenia składnika Web Part przy użyciu szablonu elementu **składnika Web Part** w programie Visual Studio 2010.

Składnik Web Part wyświetla pracowników w siatce danych. Użytkownik określa lokalizację pliku, który zawiera dane pracownika. Użytkownik może również filtrować siatkę danych, tak aby pracownicy, którzy są menedżerami, pojawiały się tylko na liście.

W instruktażu przedstawiono następujące zagadnienia:

- Tworzenie składnika Web Part przy użyciu szablonu elementu **składnika Web Part** programu Visual Studio.

- Tworzenie właściwości, którą można ustawić przez użytkownika części sieci Web. Ta właściwość określa lokalizację pliku danych pracownika.

- Renderowanie zawartości w składniku Web Part przez dodanie formantów do kolekcji formantów części sieci Web.

- Tworzenie nowego elementu menu, zwanego *czasownikiem,* który pojawia się w menu czasowniks renderowanego składnika Web Part. Zlecenia umożliwiają użytkownikowi modyfikowanie danych, które pojawiają się w składniku Web Part.

- Testowanie części sieci Web w programie SharePoint.

    > [!NOTE]
    > Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Wymagania wstępne

- Obsługiwane wersje systemu Microsoft Windows i programu SharePoint.

- Program Visual Studio 2017 lub Azure DevOps Services.

## <a name="create-an-empty-sharepoint-project"></a>Utwórz pusty projekt programu SharePoint

Najpierw utwórz pusty projekt programu SharePoint. Później dodasz składnik Web Part do projektu za pomocą szablonu elementu **składnika Web Part** .

1. Rozpocznij [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] przy użyciu opcji **Uruchom jako administrator** .

2. Na pasku mężczyźni wybierz pozycję **plik**  > **Nowy**  > **projekt**.

3. W oknie dialogowym **Nowy projekt** rozwiń węzeł **SharePoint** w języku, którego chcesz użyć, a następnie wybierz węzeł **2010** .

4. W okienku **Szablony** wybierz pozycję **projekt programu SharePoint 2010**, a następnie wybierz przycisk **OK** .

     Zostanie wyświetlony **Kreator dostosowania programu SharePoint** . Ten Kreator umożliwia wybranie lokacji, która będzie używana do debugowania projektu i poziomu zaufania rozwiązania.

5. Wybierz przycisk opcji **Wdróż jako rozwiązanie farmy** , a następnie wybierz przycisk **Zakończ** , aby zaakceptować domyślną lokalną witrynę programu SharePoint.

## <a name="add-a-web-part-to-the-project"></a>Dodawanie części sieci Web do projektu

Dodaj element **składnika Web Part** do projektu. Element **składnika Web Part** dodaje plik kodu składnika Web Part. Później dodasz kod do pliku kodu składnika Web Part w celu renderowania zawartości składnika Web Part.

1. Na pasku menu wybierz **projekt**  > **Dodaj nowy element**.

2. W oknie dialogowym **Dodaj nowy element** w okienku **zainstalowane szablony** rozwiń węzeł **SharePoint** , a następnie wybierz węzeł **2010** .

3. Na liście szablonów programu SharePoint wybierz szablon **składnik Web Part** , a następnie wybierz przycisk **Dodaj** .

     Element **składnika Web Part** pojawia się w **Eksplorator rozwiązań**.

## <a name="rendering-content-in-the-web-part"></a>Renderowanie zawartości w składniku Web Part

Możesz określić, które kontrolki mają być wyświetlane w składniku Web Part, dodając je do kolekcji Controls klasy Web Part.

1. W **Eksplorator rozwiązań**Otwórz *WebPart1. vb* (w Visual Basic) lub *WebPart1.cs* (in C#).

     Plik kodu składnika Web Part zostanie otwarty w edytorze kodu.

2. Dodaj następujące dyrektywy na początku pliku kodu składnika Web Part.

     [!code-csharp[SP_WebPart#1](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#1)]
     [!code-vb[SP_WebPart#1](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#1)]

3. Dodaj następujący kod do klasy `WebPart1`. Ten kod deklaruje następujące pola:

   - Siatka danych służąca do wyświetlania pracowników w składniku Web Part.

   - Tekst wyświetlany w kontrolce, która jest używana do filtrowania siatki danych.

   - Etykieta, która wyświetla błąd, jeśli siatka danych nie może wyświetlić danych.

   - Ciąg, który zawiera ścieżkę pliku danych pracownika.

     [!code-csharp[SP_WebPart#2](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#2)]
     [!code-vb[SP_WebPart#2](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#2)]

4. Dodaj następujący kod do klasy `WebPart1`. Ten kod dodaje niestandardową właściwość o nazwie `DataFilePath` do składnika Web Part. Właściwość niestandardowa jest właściwością, którą użytkownik może ustawić w programie SharePoint. Ta właściwość pobiera i ustawia lokalizację pliku danych XML, który jest używany do wypełniania siatki danych.

     [!code-csharp[SP_WebPart#3](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#3)]
     [!code-vb[SP_WebPart#3](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#3)]

5. Zastąp metodę `CreateChildControls` poniższym kodem. Kod będzie wykonywał następujące zadania:

   - Dodaje siatkę danych i etykietę zadeklarowaną w poprzednim kroku.

   - Tworzy powiązanie siatki danych z plikiem XML zawierającym dane pracownika.

     [!code-csharp[SP_WebPart#4](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#4)]
     [!code-vb[SP_WebPart#4](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#4)]

6. Dodaj następującą metodę do klasy `WebPart1`. Kod będzie wykonywał następujące zadania:

   - Tworzy zlecenie, które pojawia się w menu zleceń części sieci dla renderowanego składnika Web Part.

   - Obsługuje zdarzenie, które jest zgłaszane, gdy użytkownik wybierze zlecenie z menu zlecenia. Ten kod filtruje listę pracowników, którzy pojawiają się w siatce danych.

     [!code-csharp[SP_WebPart#5](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#5)]
     [!code-vb[SP_WebPart#5](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#5)]

## <a name="test-the-web-part"></a>Testowanie składnika Web Part

Po uruchomieniu projektu zostanie otwarta witryna programu SharePoint. Składnik Web Part jest automatycznie dodawany do galerii składników Web Part w programie SharePoint. Możesz dodać składnik Web Part do dowolnej strony składników Web Part.

1. Wklej następujący kod XML do pliku Notatnik. Ten plik XML zawiera przykładowe dane, które pojawią się w części sieci Web.

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

2. W programie Notepad na pasku menu wybierz pozycję **plik**  > **Zapisz jako**.

3. W oknie dialogowym **Zapisz jako** na liście **Zapisz jako typ** wybierz pozycję **wszystkie pliki**.

4. W polu **Nazwa pliku** wprowadź **dane. XML**.

5. Wybierz dowolny folder za pomocą przycisku **Przeglądaj foldery** , a następnie wybierz przycisk **Zapisz** .

6. W programie Visual Studio, wybierz klawisz **F5** .

     Zostanie otwarta witryna programu SharePoint.

7. W menu **Akcje witryny** wybierz polecenie **więcej opcji**.

8. Na stronie **Tworzenie** wybierz typ **strony składnika Web Part** , a następnie wybierz przycisk **Utwórz** .

9. Na stronie **Nowy składnik Web Part** Nazwij stronę **SampleWebPartPage. aspx**, a następnie wybierz przycisk **Utwórz** .

     Zostanie wyświetlona strona składnik Web Part.

10. Wybierz dowolną strefę na stronie składnika Web Part.

11. W górnej części strony wybierz kartę **Wstawianie** , a następnie wybierz przycisk **składnik Web Part** .

12. W okienku **Kategorie** wybierz folder **niestandardowy** , wybierz składnik Web Part **WebPart1** , a następnie wybierz przycisk **Dodaj** .

     Składnik Web Part pojawia się na stronie.

## <a name="test-the-custom-property"></a>Testowanie właściwości niestandardowej

Aby wypełnić siatkę danych, która pojawia się w składniku Web Part, określ ścieżkę pliku XML, który zawiera dane dotyczące każdego pracownika.

1. Wybierz strzałkę, która pojawia się po prawej stronie składnika Web Part, a następnie wybierz pozycję **Edytuj składnik Web Part** z wyświetlonego menu.

     Okienko zawierające właściwości składnika Web Part pojawia się po prawej stronie strony.

2. W okienku rozwiń węzeł **różne** , wprowadź ścieżkę pliku XML, który został utworzony wcześniej, wybierz przycisk **Zastosuj** , a następnie wybierz przycisk **OK** .

     Sprawdź, czy w składniku Web Part pojawia się lista pracowników.

## <a name="test-the-web-part-verb"></a>Testowanie zlecenia składnika Web Part

Pokaż i Ukryj pracowników, którzy nie są menedżerami, klikając element, który pojawia się w menu zleceń składnika Web Part.

1. Wybierz strzałkę, która pojawia się po prawej stronie składnika Web Part, a następnie wybierz pozycję **Pokaż menedżerów tylko** z wyświetlonego menu.

     W składniku Web Part są wyświetlane tylko pracownicy, którzy są menedżerami.

2. Ponownie wybierz strzałkę, a następnie wybierz **Pokaż wszystkich pracowników** z wyświetlonego menu.

     Wszyscy pracownicy są wyświetlani w składniku Web Part.

## <a name="see-also"></a>Zobacz także

[Tworzenie składników Web Part dla programu sharepoint](../sharepoint/creating-web-parts-for-sharepoint.md) 
[instrukcje: Tworzenie składnika Web part programu SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md) 
[instrukcje: Tworzenie składnika Web Part programu SharePoint za pomocą projektanta](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) 
[Przewodnik: Tworzenie składnika Web Part dla programu SharePoint za pomocą projektanta](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)
