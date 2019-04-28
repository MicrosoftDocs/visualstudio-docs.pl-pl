---
title: 'Przewodnik: LinqToXmlDataBinding Example'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: aedf42e8-896c-48fa-88df-7f7c9536aa69
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 67031266ce9b2ded595ab448d7c45674932b8751
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62892548"
---
# <a name="walkthrough-linqtoxmldatabinding-example"></a>Przewodnik: LinqToXmlDataBinding example
Ten przewodnik zawiera opis elementu linqtoxmldatabinding — przykład i omówiono bardziej interesującej zawartości dwóch plików podstawowym źródłem *L2DBForm.xaml* i *L2DBForm.xaml.cs*.

## <a name="prerequisites"></a>Wymagania wstępne
 Przed przeczytaniem tego przewodnika, firma Microsoft zdecydowanie zaleca się tworzenie, a następnie uruchom program elementu linqtoxmldatabinding — zgodnie z opisem w [jak: Kompilowanie i uruchamianie elementu linqtoxmldatabinding — przykład](../designers/how-to-build-and-run-the-linqtoxmldatabinding-example.md).

## <a name="remarks"></a>Uwagi
 Program elementu linqtoxmldatabinding — jest aplikacją Windows Presentation Foundation (WPF), który składa się języka C# i XAML, pliki źródłowe. Zawiera ona osadzonego dokumentu XML, który definiuje listy książek i umożliwia użytkownikowi wyświetlanie, dodawanie, usuwanie i edytowanie te wpisy. Składa się z następujących dwóch pliki podstawowego źródła:

- *L2DBForm.XAML* zawiera kod XAML deklaracji interfejsu użytkownika (UI) głównego okna. Zawiera ona także sekcji zasobów okna definiujący dostawcy danych i osadzonego dokumentu XML list książki.

- *L2DBForm.XAML.cs* zawiera inicjowanie i metod obsługi zdarzeń skojarzonych z interfejsu użytkownika.

  Okno główne jest podzielony na następujące cztery pionowy części interfejsu użytkownika:

- **XML** Wyświetla pierwotne źródła XML listy osadzone książki.

- **Zarezerwuj listy** Wyświetla wpisy książki jako standardowy tekst i umożliwia użytkownikowi wybierz i Usuń poszczególne wpisy.

- **Edytuj wybraną książkę** umożliwia użytkownikowi edytowanie wartości skojarzone z pozycji obecnie wybranego książki.

- **Dodawanie nowej książki** włącza funkcję tworzenia nowego wpisu książki na podstawie wartości wprowadzonej przez użytkownika.

## <a name="in-this-section"></a>W tej sekcji

|Temat|Opis|
|-----------|-----------------|
|[Kod źródłowy L2DBForm.xaml](../designers/l2dbform-xaml-source-code.md)|Zawiera opis kodu XAML w pliku L2DBForm.xaml i zawartość.|
|[Kod źródłowy L2DBForm.xaml.cs](../designers/l2dbform-xaml-cs-source-code.md)|Zawiera opis kodu źródłowego języka C# w pliku L2DBForm.xaml.cs i zawartość.|

## <a name="see-also"></a>Zobacz także

- [Powiązanie danych WPF za pomocą LINQ to XML — przykład](../designers/wpf-data-binding-using-linq-to-xml-example.md)
- [Instrukcje: Kompilowanie i uruchamianie elementu linqtoxmldatabinding — przykład](../designers/how-to-build-and-run-the-linqtoxmldatabinding-example.md)