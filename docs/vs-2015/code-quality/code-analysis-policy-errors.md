---
title: Błędy zasad analizy kodu | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.policyfailures
helpviewer_keywords:
- policy errors, code analysis
ms.assetid: d1f221cd-68c0-4277-9397-b76ad0dbae77
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 9b61d7d9718e9557ef153474718542f889ad7629
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62576745"
---
# <a name="code-analysis-policy-errors"></a>Błędy zasad analizy kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zasady analizy kodu nie jest spełniony podczas ewidencjonowania występować następujące błędy:  
  
 **Ustawienia analizy kodu dla jednego lub więcej projektów nie są zgodne z zasadami analizy kodu.**  
  
 Wymagania dotyczące analizy kodu, ewidencjonowanie do kontroli źródła projektu zespołowego nie zostało spełnione dla jednego lub więcej projektów kodu. Ten błąd może być spowodowany przez jedną lub więcej z następujących warunków:  
  
1. Nie włączono analizy kodu podczas kompilacji dla wszystkich projektów w rozwiązaniu.  
  
2. Zestaw dla projektu w programie Visual Studio ma mniej restrykcyjnych reguł lokalnych **akcji** ustawienie niż zestawu reguł projektu zespołowego na przykład regułę, która jest ustawiona na **akcji**=**błąd**  na serwerze ma jego **akcji** równa **ostrzeżenie** lub **Brak** w regule ustawić są uruchamiane w programie Visual Studio).  
  
3. Zestaw określony w programie Visual Studio reguł nie zawiera wszystkich reguł, które są określone w regule ustawić określoną w zasad ewidencjonowania analizy kodu dla projektu zespołowego.  
  
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
  
   W [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], aktywnej konfiguracji nie po włączeniu analizy kodu, ale występuje po włączeniu analizy co najmniej jeden kod.  
  
   **Należy włączyć analizy kodu dla zarządzanych danych binarnych w projekcie {0} właściwości i kompilacji przed zaewidencjonowaniem.**  
  
   Ten błąd dotyczy [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] aplikacji .NET. Zasady wymaga analizy kodu zarządzanego do wykonania, ale nie jest włączone w bieżącym projekcie na komputerze klienckim.  
  
   **Należy włączyć analizy kodu w projekcie {0} właściwości i kompilacji przed zaewidencjonowaniem.**  
  
   Ten błąd dotyczy [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektów i projektów sieci Web. Zasady wymaga analizy kodu zarządzanego do wykonania, ale nie jest włączone w bieżącym projekcie na komputerze klienckim.  
  
   **Analiza kodu C/C++ należy włączyć w projekcie {0} właściwości i kompilacji przed zaewidencjonowaniem.**  
  
   Ten błąd ma zastosowanie do projektów niezarządzanych. Zasady analizy kodu wymagają analizy kodu C/c++, ale nie jest włączone w bieżącym projekcie na komputerze klienckim.  
  
## <a name="see-also"></a>Zobacz też  
 [Błędy zgłaszane przez aplikację do analizy kodu](../code-quality/code-analysis-application-errors.md)
