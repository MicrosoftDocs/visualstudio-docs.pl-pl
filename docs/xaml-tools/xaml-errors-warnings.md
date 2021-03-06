---
title: Błędy i ostrzeżenia XAML
description: Informacje o błędach i ostrzeżeniach języka XAML w programie Visual Studio, w tym o sposobie kategoryzowania błędów, sposobach uzyskiwania informacji o błędach i sposobach ich rozwiązywania.
ms.custom: SEO-VS-2020
ms.date: 03/06/2018
ms.topic: error-reference
ms.assetid: 34eac8a0-7ec5-4c40-b97a-0126ed367931
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e33cdc11eb5531fd2325bd90912dc22a105711c5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903651"
---
# <a name="xaml-errors-and-warnings"></a>Błędy i ostrzeżenia XAML

Podczas tworzenia języka XAML program Visual Studio analizuje kod w trakcie wpisywania. W wierszu kodu pojawia się zygzak, gdy zostanie wykryty błąd. Umieszczenie kursora na zygzaku daje więcej informacji o błędzie lub ostrzeżeniu. W przypadku niektórych błędów i ostrzeżeń jest wyświetlana szybka akcja żarówki, a przy użyciu **klawisza Ctrl** + **.** skrót klawiaturowy wyświetla opcje rozwiązania problemu.

## <a name="error-types"></a>Typy błędów

W tle wiele narzędzi analizuje równolegle kod XAML. Błędy XAML są podzielone na jeden z trzech następujących typów, w oparciu o narzędzie, które wykryło błąd:

|**Błąd wykryty przez**|**Format kodu błędu**|**Wersja programu Visual Studio**|
| - |-----------------| - |
|Usługa języka XAML (Edytor XAML)|XLSxxxx| Wszystkie wersje |
|XAML Designer|XDGxxxx| Wszystkie wersje | 
|Tryb edytuj i kontynuuj języka XAML|XECxxxx| Visual Studio 2019 w wersji 16,1 lub starszej |
|Ponowne ładowanie przy aktywnym kodzie XAML | XHRxxxx | Visual Studio 2019 w wersji 16,2 lub nowszej |

Aby uzyskać więcej informacji na temat ponownego znakowania edycji XAML & Kontynuuj jako gorąca wersja XAML, zobacz [Informacje o wersji](/visualstudio/releases/2019/release-notes-v16.2#wpfuwp-tooling)

> [!Note]
> Nie wszystkie błędy lub ostrzeżenia mają odpowiedni kod. Takie błędy są zwykle projektant XAML błędów.

## <a name="suppress-xaml-designer-errors"></a>Pomijaj błędy projektant XAML

Otwórz okno dialogowe **Opcje** , wybierając polecenie **Narzędzia > opcje**, a następnie wybierz pozycję **Edytor tekstu > XAML > różne**.

Usuń zaznaczenie pola wyboru **Pokaż błędy wykryte przez PROJEKTANTA XAML** .

![Pomijaj błędy projektant XAML](media/suppress_xaml_designer_errors.png)