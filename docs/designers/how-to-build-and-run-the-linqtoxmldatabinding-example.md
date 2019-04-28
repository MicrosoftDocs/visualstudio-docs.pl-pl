---
title: 'Instrukcje: Kompilowanie i uruchamianie elementu linqtoxmldatabinding — przykład'
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 846b71b768d5b1909f29c8135616714d0124193c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62897562"
---
# <a name="how-to-build-and-run-the-linqtoxmldatabinding-example"></a>Instrukcje: Kompilowanie i uruchamianie elementu LinqToXmlDataBinding — przykład

W tym temacie pokazano, jak utworzyć i skompilować projekt programu Visual Studio elementu linqtoxmldatabinding — oraz jak uruchomić wynikowy program przykład elementu linqtoxmldatabinding — Windows Presentation Foundation (WPF).

Aby uzyskać więcej informacji na temat programu Visual Studio, zobacz [Omówienie środowiska IDE programu Visual Studio](../get-started/visual-studio-ide.md).

## <a name="create-the-project"></a>Utwórz projekt

1. Otwórz program Visual Studio i Utwórz C# **aplikacja WPF** o nazwie **elementu linqtoxmldatabinding —**. Projekt powinien skierowane do .NET Framework 3.5 (lub nowszy).

1. Jeśli nie zrobiono, dodaj odwołania do projektu dla następujących zestawów platformy .NET:

    - System.Data

    - System.Data.DataSetExtensions

    - System.Xml

    - System.Xml.Linq

1. Skompiluj rozwiązanie, naciskając klawisz **Ctrl**+**Shift**+**B**, uruchom ją, naciskając klawisz **F5**. Projekt, należy skompilować bez błędów i Uruchom jako ogólnego aplikacji WPF.

## <a name="add-code-to-the-project"></a>Dodaj kod do projektu

1. W **Eksploratora rozwiązań**, Zmień nazwę pliku źródłowego **Window1.xaml** do **L2XDBForm.xaml**. Plik źródłowy zależne **Window1.xaml.cs** automatycznie powinna zostać zmieniona na **L2XDBForm.xaml.cs**.

1. Zastąp kod źródłowy znajdującą się w pliku **L2XDBForm.xaml** z sekcji kod z tematu [kod źródłowy L2DBForm.xaml](../designers/l2dbform-xaml-source-code.md). Użyj widoku kodu XAML do pracy z tym plikiem.

1. Podobnie, Zastąp źródła w **L2XDBForm.xaml.cs** z kodem w [kod źródłowy L2DBForm.xaml.cs](../designers/l2dbform-xaml-cs-source-code.md).

1. W pliku **App.xaml**, Zamień wszystkie wystąpienia ciągu `Window1.xaml` z `L2XDBForm.xaml`.

1. Skompiluj rozwiązanie, naciskając klawisz **Ctrl**+**Shift**+**B**.

## <a name="run-the-program"></a>Uruchom program

Program elementu linqtoxmldatabinding — umożliwia użytkownikowi wyświetlanie i manipulowanie listę książek, które są przechowywane jako osadzonego elementu XML.

### <a name="to-run-the-program-and-view-the-book-list"></a>Aby uruchomić program i wyświetlić listy książek

Uruchamianie elementu linqtoxmldatabinding —, naciskając klawisz **F5** (**Rozpocznij debugowanie**) lub **Ctrl**+**F5** (**Start Bez debugowania**). Okno programu z tytułem **powiązanie danych WPF za pomocą LINQ to XML** pojawia się.

- Zwróć uwagę, w górnej części interfejsu użytkownika, wyświetla nieprzetworzonych **XML** reprezentujący listy książek. Jest wyświetlana przy użyciu technologii WPF <xref:System.Windows.Controls.TextBlock> formant, który nie obsługuje interakcji za pomocą myszy lub klawiatury.

- Druga sekcja pionowy, o nazwie **listy książek**, wyświetla Lista uporządkowana książki w postaci zwykłego tekstu. Używa ona <xref:System.Windows.Controls.ListBox> kontrolkę umożliwiającą wybór jednak myszy lub klawiatury.

### <a name="to-add-and-delete-books-from-the-list"></a>Dodawanie i usuwanie książek z listy

- Aby dodać nowej książki do listy, wprowadź wartości w **identyfikator** i **wartość** <xref:System.Windows.Controls.TextBox> kontrolek w ostatniej sekcji **Dodawanie nowej książki**, następnie kliknij przycisk **Dodaj Książki** przycisku. Należy pamiętać, że książki jest dołączany do listy w książce i ofert XML. Ten program nie można zweryfikować wartości wejściowych.

- Aby usunąć istniejącej na liście, wybierz ją w **listy książek** sekcji, a następnie kliknij przycisk **usunąć wybrane książki** przycisku. Należy zauważyć, że wpis książki została usunięta z książki i raw ofert źródła XML.

### <a name="to-edit-an-existing-book-entry"></a>Aby edytować istniejący wpis książki

1. Wybierz wpis książki w drugim **listy książek** sekcji. Jego bieżące wartości powinna być wyświetlana w sekcji trzeci **Edytuj wybrane książki**.

1. Edytuj wartości za pomocą klawiatury. Jak najszybciej albo <xref:System.Windows.Controls.TextBox> formant utraci fokus, zmiany są automatycznie propagowane do ofert źródła i książki XML.

## <a name="see-also"></a>Zobacz także

- [Powiązanie danych WPF za pomocą LINQ to XML — przykład](../designers/wpf-data-binding-using-linq-to-xml-example.md)
- [Przewodnik: LinqToXmlDataBinding example](../designers/walkthrough-linqtoxmldatabinding-example.md)
- [Visual Studio IDE — omówienie](../get-started/visual-studio-ide.md)