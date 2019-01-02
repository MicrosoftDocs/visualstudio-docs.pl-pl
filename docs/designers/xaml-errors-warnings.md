---
title: XAML błędy i ostrzeżenia
ms.date: 03/06/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 34eac8a0-7ec5-4c40-b97a-0126ed367931
author: karann-msft
ms.author: karann
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a7e0a5b4bde839e90bcf852273fa0872b1a5c76f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53922615"
---
# <a name="xaml-errors-and-warnings"></a>Błędy i ostrzeżenia XAML

Podczas tworzenia zawartości XAML, program Visual Studio analizuje kod podczas wpisywania. Fala pojawi się w wierszu kodu, gdy zostanie wykryty błąd. Kursor wężyk daje więcej informacji na temat błędu lub ostrzeżenia. Niektóre błędy i ostrzeżenia żarówki szybka akcja zostanie wyświetlony, przy użyciu **Ctrl**+**.** skrót klawiaturowy Wyświetla opcje, aby rozwiązać ten problem.

## <a name="error-types"></a>Typy błędów

W tle wielu narzędzi do analizowania XAML równolegle. Błędy XAML są podzielone na jeden z trzech następujących typów, oparte na narzędziu, że wykryto błąd:

|**Błąd wykryte przez**|**Błąd formatu kodu**|
| - |-----------------|
|Usługa języka XAML (Edytor XAML)|XLSxxxx|
|XAML Designer|XDGxxxx|
|XAML Edytuj i Kontynuuj|XECxxxx|

> [!Note]
> Nie wszystkie błędy i ostrzeżenia mają odpowiedni kod. Takie błędy są zazwyczaj błędy projektanta XAML.


## <a name="suppress-xaml-designer-errors"></a>Pomiń błędy projektanta XAML

Otwórz **opcje** okna dialogowego wybierając **Narzędzia > Opcje**, a następnie wybierz pozycję **Edytor tekstu > XAML > różne**.

Usuń zaznaczenie pola wyboru **Pokaż błędy wykryte przez projektanta XAML** pole wyboru.

![Pomiń błędy projektanta XAML](../designers/media/suppress_xaml_designer_errors.png)
