---
title: Ostrzeżenia dotyczące kryptografii
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
ms.assetid: d96723ea-a293-488d-b9db-adb437e50cdd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bff3ffef284c0cbf1503d573ba01c7a88c1c5e95
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53964179"
---
# <a name="cryptography-warnings"></a>Ostrzeżenia dotyczące kryptografii
Ostrzeżenia dotyczące kryptografii obsługują bezpieczniejsze biblioteki i aplikacje przy użyciu poprawnego użycia kryptografii. Ostrzeżenia te pomagają zapobiec usterkom w zabezpieczeniach w programie. Przyczynę wyłączenia któregokolwiek z tych ostrzeżeń należy wyraźnie oznaczyć w kodzie i poinformować o tym osobę odpowiedzialną za bezpieczeństwo w projekcie.

|Reguła|Opis|
|----------|-----------------|
|[CA5350: Nie używaj słabych algorytmów kryptograficznych](../code-quality/ca5350-do-not-use-weak-cryptographic-algorithms.md)|Słabe szyfrowanie, algorytmy i funkcje wyznaczania wartości skrótu są używane obecnie do szeregu przyczyn, ale nie powinny być używane, aby zagwarantować poufność ani spójność danych, które chronią.        Ta zasada wyzwala, gdy znajdzie TripleDES, SHA1 lub RIPEMD160 algorytmów w kodzie.|
|[CA5351: Nie używaj uszkodzonych algorytmów kryptograficznych](../code-quality/ca5351-do-not-use-broken-cryptographic-algorithms.md)|Uszkodzony kryptograficznych algorytmy nie są uznawane za bezpieczne i ich użycie powinno być zdecydowanie odradzane. Ta zasada wyzwala, gdy znajdzie algorytmu wyznaczania wartości skrótu MD5 lub DES lub RC2 algorytmów szyfrowania w kodzie.|