---
title: 'Przewodnik: Wyświetlanie etykietek narzędzi Szybkieinfo | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - QuickInfo
ms.assetid: 23fb8384-4f12-446f-977f-ce7910347947
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ef70f9a776163419819e2283a031261c6e84a159
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60076365"
---
# <a name="walkthrough-display-quickinfo-tooltips"></a>Przewodnik: Wyświetlanie etykietek narzędzi Szybkieinfo
Skrócone informacje jest funkcja IntelliSense, który wyświetla podpisy metod i opisy, gdy użytkownik przesuwa wskaźnik myszy nad nazwą metody. Definiowanie identyfikatory, które zawierają opisy skrócone informacje, a następnie tworząc etykietka narzędzia, w której chcesz wyświetlić zawartość można zaimplementować opartych na języku funkcje, takie jak skrócone informacje. Można zdefiniować skrócone informacje w kontekście usługi językowej, można zdefiniować własny plik Nazwa rozszerzenia i zawartości typ i wyświetlić skrócone informacje dla właśnie tego typu lub skrócone informacje może wyświetlać dla istniejącego typu zawartości (na przykład "text"). W tym instruktażu przedstawiono sposób wyświetlenia sekcji szybkich informacji dla typu zawartości "text".

 W przykładzie skrócone informacje w tym przewodniku Wyświetla etykietki narzędzi, gdy użytkownik przesuwa wskaźnik myszy nad nazwą metody. Ten projekt wymaga implementują te interfejsy cztery:

- interfejs źródłowy

- interfejs dostawcy źródła

- Kontroler interfejsu

- Kontroler interfejsu dostawcy

  Dostawcy źródła i kontroler Managed Extensibility Framework (MEF) składające się jest odpowiedzialny za eksportowanie klas źródłowych i kontroler i importowanie usług i brokerzy, takich jak <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>, która tworzy tekst etykietki narzędzia bufor i <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>, która wyzwala sesji skrócone informacje.

  W tym przykładzie źródło skrócone informacje używa stałej listy nazwy metod i opisów, ale w pełnej implementacji usługi językowej i dokumentacji języka są odpowiedzialne za świadczenie tej zawartości.

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, nie trzeba instalować programu Visual Studio SDK z Centrum pobierania. Został on uwzględniony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [instalacji programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Utwórz projekt MEF

### <a name="to-create-a-mef-project"></a>Aby utworzyć projekt MEF

1. Utwórz projekt VSIX języka C#. (W **nowy projekt** okno dialogowe, wybierz opcję **Visual C# / rozszerzalności**, następnie **projekt VSIX**.) Nazwij rozwiązanie `QuickInfoTest`.

2. Dodaj szablon elementu edytora klasyfikatora do projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą szablonu elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Usuń istniejące pliki klasy.

## <a name="implement-the-quickinfo-source"></a>Implementowanie źródła skrócone informacje
 Źródło sekcji szybkich informacji jest odpowiedzialny za zbieranie zbiór identyfikatorów i ich opisy i dodawanie zawartości do buforu tekstu etykietki narzędzia w przypadku jednego z identyfikatorów. W tym przykładzie identyfikatory oraz ich opisy są dodawane tylko w Konstruktorze źródła.

#### <a name="to-implement-the-quickinfo-source"></a>Aby zaimplementować źródła skrócone informacje

1. Dodaj plik klasy i nadaj mu nazwę `TestQuickInfoSource`.

2. Dodaj odwołanie do *Microsoft.VisualStudio.Language.IntelliSense*.

3. Dodaj następujące instrukcje importu.

     [!code-vb[VSSDKQuickInfoTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_1.vb)]
     [!code-csharp[VSSDKQuickInfoTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_1.cs)]

4. Deklarowanie klasy, która implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>i nadaj mu nazwę `TestQuickInfoSource`.

     [!code-vb[VSSDKQuickInfoTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_2.vb)]
     [!code-csharp[VSSDKQuickInfoTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_2.cs)]

5. Dodawanie pól do sekcji szybkich informacji dostawcy źródła, bufor tekstowy i zestaw nazwy metod i podpisy metod. W tym przykładzie nazwy metod i podpisy są inicjowane w `TestQuickInfoSource` konstruktora.

     [!code-vb[VSSDKQuickInfoTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_3.vb)]
     [!code-csharp[VSSDKQuickInfoTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_3.cs)]

6. Dodaj Konstruktor, który ustawia dostawcy źródła sekcji szybkich informacji i bufor tekstowy i wypełnia zestaw nazwy metod i podpisy metod i opisy.

     [!code-vb[VSSDKQuickInfoTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_4.vb)]
     [!code-csharp[VSSDKQuickInfoTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_4.cs)]

7. Implementowanie <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A> metody. W tym przykładzie metoda znajdzie bieżącego słowa lub poprzedniego wyrazu, jeśli kursor znajduje się na końcu wiersza lub bufor tekstowy. Jeśli słowo jest jednym z nazwy metody, opis dla tej nazwy metody jest dodawany do zawartości sekcji szybkich informacji.

     [!code-vb[VSSDKQuickInfoTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_5.vb)]
     [!code-csharp[VSSDKQuickInfoTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_5.cs)]

8. Należy także zaimplementować metodę Dispose(), ponieważ <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> implementuje <xref:System.IDisposable>:

     [!code-vb[VSSDKQuickInfoTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_6.vb)]
     [!code-csharp[VSSDKQuickInfoTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_6.cs)]

## <a name="implement-a-quickinfo-source-provider"></a>Implementowanie dostawcy źródła skrócone informacje
 Dostawca źródła skrócone informacje służy głównie w celu eksportowania się jako składnik MEF i utworzyć wystąpienie źródła skrócone informacje. Ponieważ jest to część MEF, można było zaimportować innych części MEF.

#### <a name="to-implement-a-quickinfo-source-provider"></a>Do implementowania dostawcy źródła skrócone informacje

1. Zadeklaruj dostawcy źródła skrócone informacje o nazwie `TestQuickInfoSourceProvider` implementującej <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>i wyeksportuj go z <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "Etykietka narzędzia skrócone informacje źródła" <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> z wcześniej = "default" i <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> z "text".

     [!code-vb[VSSDKQuickInfoTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_7.vb)]
     [!code-csharp[VSSDKQuickInfoTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_7.cs)]

2. Importowanie dwóch usług edytora i <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> i <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>, jako właściwości `TestQuickInfoSourceProvider`.

     [!code-vb[VSSDKQuickInfoTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_8.vb)]
     [!code-csharp[VSSDKQuickInfoTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_8.cs)]

3. Implementowanie <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A> zwracać nową `TestQuickInfoSource`.

     [!code-vb[VSSDKQuickInfoTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_9.vb)]
     [!code-csharp[VSSDKQuickInfoTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_9.cs)]

## <a name="implement-a-quickinfo-controller"></a>Implementuje kontroler skrócone informacje
 Kontrolery skrócone informacje określają, kiedy jest wyświetlany skrócone informacje. W tym przykładzie sekcji szybkich informacji jest wyświetlany, gdy wskaźnik znajduje się nad programu word, który odpowiada jednej nazwy metody. Kontroler skrócone informacje implementuje wyzwalającego sesji skrócone informacje obsługi zdarzenia po wskazaniu wskaźnikiem myszy.

### <a name="to-implement-a-quickinfo-controller"></a>Aby zaimplementować kontrolera skrócone informacje

1. Deklarowanie klasy, która implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController>i nadaj mu nazwę `TestQuickInfoController`.

     [!code-vb[VSSDKQuickInfoTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_10.vb)]
     [!code-csharp[VSSDKQuickInfoTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_10.cs)]

2. Dodaj pola prywatne dla widoku tekstu buforów tekstu reprezentowane w widoku tekstu, sesji w sekcji szybkich informacji i dostawcy kontrolera skrócone informacje.

     [!code-vb[VSSDKQuickInfoTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_11.vb)]
     [!code-csharp[VSSDKQuickInfoTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_11.cs)]

3. Dodaj Konstruktor, który ustawia pola i dodaje program obsługi zdarzeń po wskazaniu wskaźnikiem myszy.

     [!code-vb[VSSDKQuickInfoTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_12.vb)]
     [!code-csharp[VSSDKQuickInfoTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_12.cs)]

4. Dodawanie obsługi zdarzeń myszy po wskazaniu wskaźnikiem, który wyzwala sesji skrócone informacje.

     [!code-vb[VSSDKQuickInfoTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_13.vb)]
     [!code-csharp[VSSDKQuickInfoTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_13.cs)]

5. Implementowanie <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A> metodę, tak że usuwa obsługi zdarzeń myszy po wskazaniu wskaźnikiem odłączeniem kontrolera widoku tekstu.

     [!code-vb[VSSDKQuickInfoTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_14.vb)]
     [!code-csharp[VSSDKQuickInfoTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_14.cs)]

6. Implementowanie <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A> metody i <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A> metodę jako puste metody w tym przykładzie.

     [!code-vb[VSSDKQuickInfoTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_15.vb)]
     [!code-csharp[VSSDKQuickInfoTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_15.cs)]

## <a name="implementing-the-quickinfo-controller-provider"></a>Implementowanie dostawcy kontrolera skrócone informacje
 Dostawca kontrolera skrócone informacje służy głównie do eksportowania się jako składnik MEF i tworzenia wystąpienia kontrolera skrócone informacje. Ponieważ jest to część MEF, można było zaimportować innych części MEF.

### <a name="to-implement-the-quickinfo-controller-provider"></a>Do implementowania dostawcy kontrolera skrócone informacje

1. Zadeklaruj klasę o nazwie `TestQuickInfoControllerProvider` implementującej <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider>i wyeksportuj go z <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "Etykietka narzędzia skrócone informacje kontrolera" i <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> z "text":

     [!code-vb[VSSDKQuickInfoTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_16.vb)]
     [!code-csharp[VSSDKQuickInfoTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_16.cs)]

2. Importuj <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> jako właściwość.

     [!code-vb[VSSDKQuickInfoTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_17.vb)]
     [!code-csharp[VSSDKQuickInfoTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_17.cs)]

3. Implementowanie <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A> metoda przez utworzenie wystąpienia kontrolera skrócone informacje.

     [!code-vb[VSSDKQuickInfoTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_18.vb)]
     [!code-csharp[VSSDKQuickInfoTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_18.cs)]

## <a name="build-and-test-the-code"></a>Tworzenie i testowanie kodu
 Aby przetestować ten kod, Kompiluj rozwiązanie QuickInfoTest, a następnie uruchomić go w doświadczalnym wystąpieniu.

### <a name="to-build-and-test-the-quickinfotest-solution"></a>Aby skompilować i przetestować rozwiązanie QuickInfoTest

1. Skompiluj rozwiązanie.

2. Po uruchomieniu tego projektu w debugerze, drugie wystąpienie programu Visual Studio został uruchomiony.

3. Utwórz plik tekstowy i wpisz jakiś tekst, który zawiera słowa "add" i "odejmowania".

4. Przesuń wskaźnik nad jednym z wystąpień "Dodaj". Podpis i opis `add` metoda powinna być wyświetlana.

## <a name="see-also"></a>Zobacz także
- [Przewodnik: Połączyć typu zawartości z rozszerzeniem nazwy pliku](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)