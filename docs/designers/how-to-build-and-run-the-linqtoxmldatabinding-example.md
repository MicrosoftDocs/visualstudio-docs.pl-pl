---
title: 'Instrukcje: kompilowanie i uruchamianie przykładu elementu LinqToXmlDataBinding —'
ms.date: 11/04/2016
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3b3999ae6fb602c9877bc3f997ab922bda08565b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72636873"
---
# <a name="how-to-build-and-run-the-linqtoxmldatabinding-example"></a>Instrukcje: kompilowanie i uruchamianie przykładu elementu LinqToXmlDataBinding —

W tym temacie pokazano, jak utworzyć i skompilować projekt programu elementu LinqToXmlDataBinding — w programie Visual Studio oraz jak uruchomić w tym celu Przykładowy program elementu LinqToXmlDataBinding — Windows Presentation Foundation (WPF).

Aby uzyskać więcej informacji na temat programu Visual Studio, zobacz [Omówienie środowiska IDE programu Visual Studio](../get-started/visual-studio-ide.md).

## <a name="create-the-project"></a>Utwórz projekt

1. Otwórz program Visual Studio i Utwórz C# **aplikację WPF** o nazwie **elementu LinqToXmlDataBinding —** .

   Projekt powinien kierować do .NET Framework 3,5 (lub nowszego).

1. Jeśli jeszcze nie istnieje, Dodaj odwołania do projektu dla następujących zestawów .NET:

    - System.Data

    - System. Data. DataSetExtensions

    - System.Xml

    - System. XML. LINQ

1. Skompiluj rozwiązanie, naciskając klawisz **Ctrl** +**SHIFT** +**B**, a następnie uruchom go, naciskając klawisz **F5**. Projekt powinien zostać skompilowany bez błędów i uruchomiony jako ogólna aplikacja WPF.

## <a name="add-code-to-the-project"></a>Dodawanie kodu do projektu

1. W **Eksplorator rozwiązań**Zmień nazwę pliku źródłowego **window1. XAML** na **L2XDBForm. XAML**. Nazwa pliku źródłowego zależnego **window1.XAML.cs** powinna być automatycznie zmieniana na **L2XDBForm.XAML.cs**.

1. Zastąp kod źródłowy znaleziony w pliku **L2XDBForm. XAML** z sekcją Code w temacie [kod źródłowy L2DBForm. XAML kod źródłowy](../designers/l2dbform-xaml-source-code.md). Użyj widoku źródła XAML do pracy z tym plikiem.

1. Podobnie zastąp źródło w **L2XDBForm.XAML.cs** kodem znalezionym w [kodzie źródłowym L2DBForm.XAML.cs](../designers/l2dbform-xaml-cs-source-code.md).

1. W pliku **App. XAML**Zamień wszystkie wystąpienia ciągu `Window1.xaml` z `L2XDBForm.xaml`.

1. Skompiluj rozwiązanie, naciskając klawisz **Ctrl** +**SHIFT** +**B**.

## <a name="run-the-program"></a>Uruchom program

Program elementu LinqToXmlDataBinding — umożliwia użytkownikowi wyświetlanie listy książek przechowywanych jako osadzony element XML i manipulowanie nimi.

### <a name="to-run-the-program-and-view-the-book-list"></a>Aby uruchomić program i wyświetlić listę książek

Uruchom elementu LinqToXmlDataBinding —, naciskając klawisz **F5** (**Rozpocznij debugowanie**) lub **Ctrl** +**F5** (**Rozpocznij bez debugowania**). Zostanie wyświetlone okno programu z tytułem **powiązania danych WPF przy użyciu LINQ to XML** .

- Zwróć uwagę na górną sekcję interfejsu użytkownika, która wyświetla nieprzetworzony **kod XML** , który reprezentuje listę książek. Jest ona wyświetlana przy użyciu kontrolki <xref:System.Windows.Controls.TextBlock> WPF, która nie umożliwia interakcji za pośrednictwem myszy lub klawiatury.

- Druga sekcja pionowa z etykietą **lista książek**zawiera książki jako listę uporządkowaną jako zwykły tekst. Używa kontrolki <xref:System.Windows.Controls.ListBox>, która umożliwia wybór za pośrednictwem myszy lub klawiatury.

### <a name="to-add-and-delete-books-from-the-list"></a>Aby dodać i usunąć książki z listy

- Aby dodać nową książkę do listy, wprowadź wartości w polu **Identyfikator** i **wartość** <xref:System.Windows.Controls.TextBox> kontrolki w ostatniej sekcji, **Dodaj nową książkę**, a następnie kliknij przycisk **Dodaj książkę** . Należy pamiętać, że książka jest dołączana do listy w listach książki i XML. Ten program nie weryfikuje wartości wejściowych.

- Aby usunąć istniejącą książkę z listy, wybierz ją w sekcji **lista książek** , a następnie kliknij przycisk **Usuń wybraną książkę** . Zwróć uwagę, że wpis książki został usunięty z list książek i nieprzetworzonych źródeł XML.

### <a name="to-edit-an-existing-book-entry"></a>Aby edytować istniejący wpis książki

1. Wybierz wpis książki w drugiej sekcji **listy książek** . Bieżące wartości powinny być wyświetlane w trzeciej sekcji **Edytuj wybraną książkę**.

1. Edytuj wartości przy użyciu klawiatury. Gdy tylko formant <xref:System.Windows.Controls.TextBox> ma swobodny fokus, zmiany są automatycznie propagowane do listy źródłowej XML i książki.

## <a name="see-also"></a>Zobacz także

- [Powiązanie danych WPF przy użyciu LINQ to XML przykładu](../designers/wpf-data-binding-using-linq-to-xml-example.md)
- [Przewodnik: elementu LinqToXmlDataBinding — przykład](../designers/walkthrough-linqtoxmldatabinding-example.md)
- [Środowisko IDE programu Visual Studio — omówienie](../get-started/visual-studio-ide.md)