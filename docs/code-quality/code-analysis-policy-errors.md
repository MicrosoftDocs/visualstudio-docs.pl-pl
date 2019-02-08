---
title: Błędy zasad analizy kodu
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.policyfailures
helpviewer_keywords:
- policy errors, code analysis
ms.assetid: d1f221cd-68c0-4277-9397-b76ad0dbae77
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 103a48172665875c3615ce57b90dc77beeb6b5c4
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55921565"
---
# <a name="code-analysis-policy-errors"></a>Błędy zasad analizy kodu

Zasady analizy kodu nie jest spełniony podczas ewidencjonowania występować następujące błędy:

**Ustawienia analizy kodu dla jednego lub więcej projektów nie są zgodne z zasadami analizy kodu.**

Wymagania dotyczące analizy kodu, ewidencjonowanie do kontroli źródła projektu nie zostało spełnione dla jednego lub więcej projektów kodu. Ten błąd może być spowodowany przez jedną lub więcej z następujących warunków:

- Nie włączono analizy kodu podczas kompilacji dla wszystkich projektów w rozwiązaniu.

- Zestaw dla projektu w programie Visual Studio ma mniej restrykcyjnych reguł lokalnych **akcji** ustawienie niż zestaw reguł projektu na przykład regułę, która jest równa **akcji**=**błąd** na serwerze ma jego **akcji** równa **ostrzeżenie** lub **Brak** w regule ustawić są uruchamiane w programie Visual Studio).

- Zestaw określony w programie Visual Studio reguł nie zawiera wszystkich reguł, które są określone w regule ustawić określoną w zasad ewidencjonowania analizy kodu dla projektu.

**Zasady analizy kodu nie powiodło się. Wystąpiły błędy w projekcie {0} lub nie jest aktualny.**

Albo kompilacji zawiera błędy lub błędy zostały usunięte, ale analiza kodu nie została wykonana po poprawki.

**Zaewidencjonowanie nie powiodło się. Zasady analizy kodu wymaga, że zaewidencjonowania za pomocą programu Visual Studio z otwartym rozwiązaniem.**

Zasady analizy kodu wymaga, że wszystkie pliki, które zostały zaewidencjonowane musi należeć do aktualnie otwartego rozwiązania. Aby rozwiązać ten problem, otwórz rozwiązanie, które zawiera plik do wyewidencjonowania.

**Nie wszystkie pliki w oknie oczekujące zaewidencjonowania znajdują się w aktualnie otwartego rozwiązania.**

Zasady analizy kodu wymaga, że wszystkie pliki, które zostały zaewidencjonowane musi należeć do aktualnie otwartego rozwiązania. Ten błąd jest wywoływane, gdy jest otwarte rozwiązanie, ale niektóre pliki w widoku "oczekujące zaewidencjonowania" nie są częścią aktualnie otwarte rozwiązanie. Aby rozwiązać ten problem, otwórz rozwiązanie, które zawiera plik do wyewidencjonowania.

**Wersja "{0}" jest nieprawidłowy. Silna nazwa-określonym w zasadach jest "{1}".**

Ten błąd ma zastosowanie do projektów .NET. Reguły plik .dll, wymagany przez zasady analizy kodu istnieje na komputerze lokalnym, ale wersja/klucz publiczny jest niezgodny. Aby naprawić ten błąd, twórcy zasad należy zaktualizować bibliotek DLL w *C:\Program Files\Microsoft Visual Studio 8\Team Tools\Static analizy Tools\FxCop\Rules\\*  katalogu na swoim komputerze.

**"{0}" nie istnieje zestaw określony w zasadach.**

Ten błąd ma zastosowanie do projektów .NET. Reguła wymagany przez zasady analizy kodu nie ma odpowiedniej biblioteki dll zainstalowany na komputerze klienckim. Aby naprawić ten błąd, twórcy zasad należy zaktualizować biblioteki dll w *C:\Program Files\Microsoft Visual Studio 8\Team Tools\Static analizy Tools\FxCop\Rules\\*  katalogu na swoim komputerze.

**Projekt {0} ustawienia reguły nie są zgodność z zasadami analizy kodu.**

Ten błąd ma zastosowanie do projektów .NET. Ustawienia reguł kodu zarządzanego nie są tak rygorystyczne zasady wymagają. Aby naprawić ten błąd, ustawienia klienta musi być taka sama lub bardziej restrykcyjny niż wymaganie zasad na serwerze.

**Nie włączono analizy kodu na aktywnej konfiguracji. Przełącz się do konfiguracji {0} i skompiluj projekt {1} przed zaewidencjonowaniem.**

W [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], aktywnej konfiguracji nie po włączeniu analizy kodu, ale występuje po włączeniu analizy co najmniej jeden kod.

**Należy włączyć analizy kodu dla zarządzanych danych binarnych w projekcie {0} właściwości i kompilacji przed zaewidencjonowaniem.**

Ten błąd dotyczy [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] aplikacji .NET. Zasady wymaga analizy kodu zarządzanego do wykonania, ale nie jest włączone w bieżącym projekcie na komputerze klienckim.

**Należy włączyć analizy kodu w projekcie {0} właściwości i kompilacji przed zaewidencjonowaniem.**

Ten błąd dotyczy [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projektów i projektów sieci web. Zasady wymaga analizy kodu zarządzanego do wykonania, ale nie jest włączone w bieżącym projekcie na komputerze klienckim.

**Analiza kodu C/C++ należy włączyć w projekcie {0} właściwości i kompilacji przed zaewidencjonowaniem.**

Ten błąd ma zastosowanie do projektów niezarządzanych. Zasady analizy kodu wymagają analizy kodu C/c++, ale nie jest włączone w bieżącym projekcie na komputerze klienckim.

## <a name="see-also"></a>Zobacz też

- [Błędy zgłaszane przez aplikację do analizy kodu](../code-quality/code-analysis-application-errors.md)