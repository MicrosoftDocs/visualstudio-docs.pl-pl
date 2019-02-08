---
title: 'CA1020: Unikaj przestrzeni nazw z małą liczbą typów'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1020
- AvoidNamespacesWithFewTypes
helpviewer_keywords:
- CA1020
- AvoidNamespacesWithFewTypes
ms.assetid: 9cb272f6-a3ff-45af-b35d-70dea620b074
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 396208b9594e46aa179c3eebddc5a552ce0fca3c
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55916664"
---
# <a name="ca1020-avoid-namespaces-with-few-types"></a>CA1020: Unikaj przestrzeni nazw z małą liczbą typów

|||
|-|-|
|TypeName|AvoidNamespacesWithFewTypes|
|CheckId|CA1020|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna

Przestrzeń nazw, innym niż globalna przestrzeń nazw zawiera mniej niż pięć typów.

## <a name="rule-description"></a>Opis reguły

Upewnij się, że każda z przestrzeni nazw posiada organizację logiczną i że istnieje uzasadniony powód, aby umieścić typy w słabo wypełnionych przestrzeniach nazw. Przestrzenie nazw może zawierać typy, które są używane razem w większości scenariuszy. Po ich aplikacje są wzajemnie się wykluczają, typy powinien znajdować się w oddzielnych przestrzeniach nazw. Na przykład <xref:System.Web.UI> przestrzeń nazw zawiera typy, które są używane w aplikacji sieci web i <xref:System.Windows.Forms> przestrzeń nazw zawiera typy, które są używane w [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)]— na podstawie aplikacji. Mimo że obie przestrzenie nazw mają typy sterujące aspektów interfejsu użytkownika, te typy nie są przeznaczone do użytku w samej aplikacji. W związku z tym znajdują się one w oddzielnych przestrzeniach nazw. Ponieważ zwiększa możliwości odnajdywania funkcji organizacji dokładnej przestrzeni nazw może być również przydatne. Sprawdzając hierarchii obszaru nazw, konsumenci biblioteki powinien móc znaleźć typy, które implementują funkcji.

> [!NOTE]
> Typy w czasie projektowania i uprawnienia nie powinny zostać scalone w innych przestrzeniach nazw, aby był zgodny z niniejszymi wytycznymi. Te typy należeć własne przestrzenie nazw poniżej głównej przestrzeni nazw, a przestrzenie nazw powinny kończyć się `.Design` i `.Permissions`, odpowiednio.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, spróbuj połączyć przestrzenie nazw, który zawiera kilka typów w jednej przestrzeni nazw.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli przestrzeń nazw zawiera typy, które są używane z typami w Twojej przestrzeni nazw.