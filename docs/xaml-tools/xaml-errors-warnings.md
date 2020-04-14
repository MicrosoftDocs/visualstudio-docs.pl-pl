---
title: Błędy i ostrzeżenia XAML
ms.date: 03/06/2018
ms.topic: conceptual
ms.assetid: 34eac8a0-7ec5-4c40-b97a-0126ed367931
author: karann-msft
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f8a36a91f40fd4857e50d5262c1598ee096697e7
ms.sourcegitcommit: 22deb247ad951e4971f27fdab413b158415d0584
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81276467"
---
# <a name="xaml-errors-and-warnings"></a>Błędy i ostrzeżenia XAML

Podczas tworzenia xaml visual studio analizuje kod podczas pisania. Squiggle pojawia się w wierszu kodu po wykryciu błędu. Najechanie kursorem na falidłanie daje więcej informacji o błędzie lub ostrzeżeniu. W przypadku niektórych błędów i ostrzeżeń wyświetlana jest żarówka szybka akcja i używająca **klawisza Ctrl**+**.** skrót klawiaturowy wyświetla opcje rozwiązania problemu.

## <a name="error-types"></a>Typy błędów

Za kulisami wiele narzędzi analizuje xaml równolegle. Błędy XAML są podzielone na jeden z następujących trzech typów, na podstawie narzędzia, które wykryło błąd:

|**Błąd wykryty przez**|**Format kodu błędu**|
| - |-----------------|
|Usługa języka XAML (edytor XAML)|XLSxxxx ( XLSxxxx )|
|XAML Designer|XDGxxxx ( XDGxxxx )|
|XAML Edytuj i kontynuuj|XECxxxx ( Xecxxxx )|

> [!Note]
> Nie wszystkie błędy lub ostrzeżenia mają odpowiedni kod. Takie błędy są zazwyczaj błędy projektanta XAML.

## <a name="suppress-xaml-designer-errors"></a>Pomijanie błędów projektanta XAML

Otwórz okno dialogowe **Opcje,** zaznaczając **pozycję Narzędzia > opcje**, a następnie wybierz pozycję Edytor tekstu > **XAML > Różne**.

Wyewidencjonuj pole wyboru **Pokaż błędy wykryte przez projektanta XAML.**

![Pomijanie błędów projektanta XAML](media/suppress_xaml_designer_errors.png)
