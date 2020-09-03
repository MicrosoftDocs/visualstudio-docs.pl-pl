---
title: Błędy i ostrzeżenia XAML
ms.date: 03/06/2018
ms.topic: error-reference
ms.assetid: 34eac8a0-7ec5-4c40-b97a-0126ed367931
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b740f0882edb2eae9f00bd7826543e7fe1b4597f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85817271"
---
# <a name="xaml-errors-and-warnings"></a>Błędy i ostrzeżenia XAML

Podczas tworzenia języka XAML program Visual Studio analizuje kod w trakcie wpisywania. W wierszu kodu pojawia się zygzak, gdy zostanie wykryty błąd. Umieszczenie kursora na zygzaku daje więcej informacji o błędzie lub ostrzeżeniu. W przypadku niektórych błędów i ostrzeżeń jest wyświetlana szybka akcja żarówki, a przy użyciu **klawisza Ctrl** + **.** skrót klawiaturowy wyświetla opcje rozwiązania problemu.

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

Otwórz okno dialogowe **Opcje** , wybierając polecenie **Narzędzia > opcje**, a następnie wybierz pozycję **Edytor tekstu > XAML > różne**.

Usuń zaznaczenie pola wyboru **Pokaż błędy wykryte przez PROJEKTANTA XAML** .

![Pomijaj błędy projektant XAML](media/suppress_xaml_designer_errors.png)
