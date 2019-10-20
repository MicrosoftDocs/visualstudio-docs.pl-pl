---
title: 'Instrukcje: kompilowanie i uruchamianie przykładu elementu LinqToXmlDataBinding — | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 3943deaf-80e2-4968-ac04-d3ef56cfad6c
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5584494f65eaef72c2aa350af4e5af36155e0501
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664627"
---
# <a name="how-to-build-and-run-the-linqtoxmldatabinding-example"></a>Instrukcje: kompilowanie i uruchamianie przykładu elementu LinqToXmlDataBinding —
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie pokazano, jak utworzyć i skompilować projekt programu elementu LinqToXmlDataBinding — w programie Visual Studio oraz jak uruchomić w tym celu Przykładowy program elementu LinqToXmlDataBinding — Windows Presentation Foundation (WPF).

 Aby uzyskać więcej informacji na temat tworzenia projektów przy użyciu programu Visual Studio, zobacz [Programowanie aplikacji w programie Visual Studio](https://msdn.microsoft.com/97490c1b-a247-41fb-8f2c-bc4c201eff68).

## <a name="creating-and-populating-the-project"></a>Tworzenie i wypełnianie projektu

#### <a name="to-create-the-starting-project"></a>Aby utworzyć projekt początkowy

1. Uruchom program Visual Studio i Utwórz C# aplikację WPF o nazwie elementu LinqToXmlDataBinding —. Projekt musi używać .NET Framework 3,5 (lub nowszego).

2. Jeśli jeszcze nie istnieje, Dodaj odwołania do projektu dla następujących zestawów .NET:

    - System.Data

    - System. Data. DataSetExtensions

    - System.Xml

    - System. XML. LINQ

3. Skompiluj rozwiązanie, naciskając pozycję **Ctnrl + Shift + B**, a następnie uruchom ją, naciskając klawisz **F5**. Projekt powinien zostać skompilowany bez błędów i uruchomiony jako ogólna aplikacja WPF.

#### <a name="to-add-custom-code-to-the-project"></a>Aby dodać niestandardowy kod do projektu

1. W Eksplorator rozwiązań Zmień nazwę pliku źródłowego window1. XAML na L2XDBForm. XAML. Nazwa pliku źródłowego zależnego Window1.xaml.cs powinna być automatycznie zmieniana na L2XDBForm.xaml.cs.

2. Zastąp kod źródłowy znaleziony w pliku L2XDBForm. XAML z sekcją Code w temacie [kod źródłowy L2DBForm. XAML kod źródłowy](../designers/l2dbform-xaml-source-code.md). (Użyj widoku źródła XAML, aby korzystać z tego pliku).

3. Podobnie zastąp źródło w L2XDBForm.xaml.cs kodem znalezionym w [kodzie źródłowym L2DBForm.XAML.cs](../designers/l2dbform-xaml-cs-source-code.md).

4. W pliku App. XAML Zamień wszystkie wystąpienia ciągu "window1. XAML" na "L2XDBForm. XAML".

5. Skompiluj rozwiązanie, naciskając **klawisze CTRL + SHIFT + B**.

## <a name="running-the-program"></a>Uruchamianie programu
 Program elementu LinqToXmlDataBinding — umożliwia użytkownikowi wyświetlanie listy książek przechowywanych jako osadzony element XML i manipulowanie nimi.

#### <a name="to-run-the-program-and-view-the-book-list"></a>Aby uruchomić program i wyświetlić listę książek

1. Uruchom elementu LinqToXmlDataBinding —, naciskając klawisz **F5** (**Rozpocznij debugowanie**) lub **Ctrl + F5** (**Rozpocznij bez debugowania**). Należy wyświetlić okno programu z tytułem **powiązania danych WPF przy użyciu LINQ to XML** .

2. Zwróć uwagę na górną sekcję interfejsu użytkownika, która wyświetla nieprzetworzony **kod XML** , który reprezentuje listę książek. Jest ona wyświetlana przy użyciu kontrolki <xref:System.Windows.Controls.TextBlock> WPF, która nie umożliwia interakcji za pośrednictwem myszy lub klawiatury.

3. Druga sekcja pionowa z etykietą **lista książek**zawiera książki jako listę uporządkowaną jako zwykły tekst. Używa kontrolki <xref:System.Windows.Controls.ListBox>, która umożliwia wybór za pośrednictwem myszy lub klawiatury.

#### <a name="to-add-and-delete-books-from-the-list"></a>Aby dodać i usunąć książki z listy

1. Aby usunąć istniejącą książkę z listy, wybierz ją w sekcji **lista książek** , a następnie kliknij przycisk **Usuń wybraną książkę** . Zwróć uwagę, że wpis książki został usunięty z list książek i nieprzetworzonych źródeł XML.

2. Aby dodać nową książkę do listy, wprowadź wartości w polu **Identyfikator** i **wartość** <xref:System.Windows.Controls.TextBox> kontrolki w ostatniej sekcji, **Dodaj nową książkę**, a następnie kliknij przycisk **Dodaj książkę** . Należy pamiętać, że książka jest dołączana do listy w listach książki i XML. Ten program nie weryfikuje wartości wejściowych.

#### <a name="to-edit-an-existing-book-entry"></a>Aby edytować istniejący wpis książki

1. Wybierz wpis książki w drugiej sekcji **listy książek** . Bieżące wartości powinny być wyświetlane w trzeciej sekcji **Edytuj wybraną książkę**.

2. Edytuj wartości przy użyciu klawiatury. Gdy tylko formant <xref:System.Windows.Controls.TextBox> ma swobodny fokus, zmiany są automatycznie propagowane do listy źródłowej XML i książki.

## <a name="see-also"></a>Zobacz też
 [Powiązanie danych WPF przy użyciu LINQ to XML przykładowego](../designers/wpf-data-binding-using-linq-to-xml-example.md) [przewodnika: elementu LinqToXmlDataBinding — przykład](../designers/walkthrough-linqtoxmldatabinding-example.md) [tworzenia aplikacji w programie Visual Studio](https://msdn.microsoft.com/97490c1b-a247-41fb-8f2c-bc4c201eff68)
