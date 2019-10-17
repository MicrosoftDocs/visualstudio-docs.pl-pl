---
title: Błędy i ostrzeżenia XAML
ms.date: 03/06/2018
ms.topic: conceptual
ms.assetid: 34eac8a0-7ec5-4c40-b97a-0126ed367931
author: karann-msft
ms.author: karann
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5d8821da877536195d44a02102d3650e1f5cee01
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72450983"
---
# <a name="xaml-errors-and-warnings"></a>Błędy i ostrzeżenia XAML

Podczas tworzenia języka XAML program Visual Studio analizuje kod w trakcie wpisywania. W wierszu kodu pojawia się zygzak, gdy zostanie wykryty błąd. Umieszczenie kursora na zygzaku daje więcej informacji o błędzie lub ostrzeżeniu. W przypadku niektórych błędów i ostrzeżeń zostanie wyświetlona szybka akcja żarówki, a przy użyciu **klawisza Ctrl**+ **.** skrót klawiaturowy wyświetla opcje rozwiązania problemu.

## <a name="error-types"></a>Typy błędów

W tle wiele narzędzi analizuje równolegle kod XAML. Błędy XAML są podzielone na jeden z trzech następujących typów, w oparciu o narzędzie, które wykryło błąd:

|**Błąd wykryty przez**|**Format kodu błędu**|
| - |-----------------|
|Usługa języka XAML (Edytor XAML)|XLSxxxx|
|XAML Designer|XDGxxxx|
|Edytuj i Kontynuuj XAML|XECxxxx|

> [!Note]
> Nie wszystkie błędy lub ostrzeżenia mają odpowiedni kod. Takie błędy są zwykle projektant XAML błędów.

## <a name="suppress-xaml-designer-errors"></a>Pomijaj błędy projektant XAML

Otwórz okno dialogowe **Opcje** , wybierając polecenie **Narzędzia > Opcje**, a następnie wybierz pozycję **Edytor tekstu > XAML > różne**.

Usuń zaznaczenie pola wyboru **Pokaż błędy wykryte przez PROJEKTANTA XAML** .

![Pomijaj błędy projektant XAML](media/suppress_xaml_designer_errors.png)
