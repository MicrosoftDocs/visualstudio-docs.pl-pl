---
title: Ostrzeżenia dotyczące kryptografii | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: d96723ea-a293-488d-b9db-adb437e50cdd
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c573d461b477bbcdc7e988ea66f03d5a7cc0fdb6
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54833892"
---
# <a name="cryptography-warnings"></a>Ostrzeżenia dotyczące kryptografii
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ostrzeżenia dotyczące kryptografii obsługują bezpieczniejsze biblioteki i aplikacje przy użyciu poprawnego użycia kryptografii. Ostrzeżenia te pomagają zapobiec usterkom w zabezpieczeniach w programie. Przyczynę wyłączenia któregokolwiek z tych ostrzeżeń należy wyraźnie oznaczyć w kodzie i poinformować o tym osobę odpowiedzialną za bezpieczeństwo w projekcie.  
  
|Reguła|Opis|  
|----------|-----------------|  
|[CA5350: Nie używaj słabych algorytmów kryptograficznych](../code-quality/ca5350-do-not-use-weak-cryptographic-algorithms.md)|Słabe szyfrowanie, algorytmy i funkcje wyznaczania wartości skrótu są używane obecnie do szeregu przyczyn, ale nie powinny być używane, aby zagwarantować poufność ani spójność danych, które chronią.        Ta zasada wyzwala, gdy znajdzie TripleDES, SHA1 lub RIPEMD160 algorytmów w kodzie.|  
|[CA5351: Nie używaj uszkodzonych algorytmów kryptograficznych](../code-quality/ca5351-do-not-use-broken-cryptographic-algorithms.md)|Uszkodzony kryptograficznych algorytmy nie są uznawane za bezpieczne i ich użycie powinno być zdecydowanie odradzane. Ta zasada wyzwala, gdy znajdzie algorytmu wyznaczania wartości skrótu MD5 lub DES lub RC2 algorytmów szyfrowania w kodzie.|
