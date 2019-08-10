---
title: 'Przewodnik: LinqToXmlDataBinding — przykład'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: aedf42e8-896c-48fa-88df-7f7c9536aa69
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c99d8571480dd98726a5f1ae5772162e97e0baed
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68925735"
---
# <a name="walkthrough-linqtoxmldatabinding-example"></a>Przewodnik: Przykład elementu LinqToXmlDataBinding —
W tym instruktażu opisano przykład elementu LinqToXmlDataBinding — i wyjaśniono niektóre z bardziej interesujących zawartości dwóch głównych plików źródłowych, *kod źródłowy L2DBForm. XAML* i *L2DBForm.XAML.cs*.

## <a name="prerequisites"></a>Wymagania wstępne
Przed przeczytaniem tego instruktażu zdecydowanie zalecamy skompilowanie i uruchomienie programu elementu LinqToXmlDataBinding — zgodnie z opisem w [temacie How to: Kompiluj i uruchamiaj przykład](../designers/how-to-build-and-run-the-linqtoxmldatabinding-example.md)elementu LinqToXmlDataBinding —.

## <a name="remarks"></a>Uwagi
 Program elementu LinqToXmlDataBinding — jest aplikacją Windows Presentation Foundation (WPF), która składa się z C# plików źródłowych i XAML. Zawiera osadzony dokument XML, który definiuje listę książek i umożliwia użytkownikowi wyświetlanie, Dodawanie, usuwanie i edytowanie tych wpisów. Składa się z następujących dwóch podstawowych plików źródłowych:

- *Kod źródłowy L2DBForm. XAML* zawiera kod deklaracji XAML dla interfejsu użytkownika okna głównego. Zawiera również sekcję zasobów okna, która definiuje dostawcę danych i osadzony dokument XML dla list książek.

- *L2DBForm.XAML.cs* zawiera metody inicjowania i obsługi zdarzeń SKOJARZONE z interfejsem użytkownika.

  Okno główne jest podzielone na następujące cztery pionowe sekcje interfejsu użytkownika:

- **Kod XML** Wyświetla pierwotne źródło XML listy osadzonych książek.

- **Lista książek** wyświetla wpisy książki jako tekst standardowy i umożliwia użytkownikowi wybranie i usunięcie poszczególnych wpisów.

- **Edycja wybranej książki** umożliwia użytkownikowi edytowanie wartości skojarzonych z aktualnie wybranym wpisem książki.

- **Dodawanie nowej książki** umożliwia tworzenie nowych wpisów książki na podstawie wartości wprowadzonych przez użytkownika.

## <a name="in-this-section"></a>W tej sekcji

|Temat|Opis|
|-----------|-----------------|
|[Kod źródłowy L2DBForm.xaml](../designers/l2dbform-xaml-source-code.md)|Zawiera zawartość i Opis kodu XAML w pliku kod źródłowy L2DBForm. XAML.|
|[Kod źródłowy L2DBForm.xaml.cs](../designers/l2dbform-xaml-cs-source-code.md)|Zawiera zawartość i Opis kodu C# źródłowego w pliku L2DBForm.XAML.cs.|

## <a name="see-also"></a>Zobacz także

- [Powiązanie danych WPF przy użyciu LINQ to XML przykładu](../designers/wpf-data-binding-using-linq-to-xml-example.md)
- [Instrukcje: Kompilowanie i uruchamianie przykładu elementu LinqToXmlDataBinding —](../designers/how-to-build-and-run-the-linqtoxmldatabinding-example.md)