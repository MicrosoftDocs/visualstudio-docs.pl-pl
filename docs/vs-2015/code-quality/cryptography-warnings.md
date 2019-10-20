---
title: Ostrzeżenia kryptografii | Microsoft Docs
ms.date: 11/15/2016
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: d96723ea-a293-488d-b9db-adb437e50cdd
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d9f5694ccf48615ebdf7157adc80543b0fbb71eb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667672"
---
# <a name="cryptography-warnings"></a>Ostrzeżenia dotyczące kryptografii
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ostrzeżenia kryptografii obsługują bezpieczniejsze biblioteki i aplikacje poprzez poprawne użycie kryptografii. Ostrzeżenia te pomagają zapobiec usterkom w zabezpieczeniach w programie. Przyczynę wyłączenia któregokolwiek z tych ostrzeżeń należy wyraźnie oznaczyć w kodzie i poinformować o tym osobę odpowiedzialną za bezpieczeństwo w projekcie.

|Reguła|Opis|
|----------|-----------------|
|[CA5350: Nie używaj słabych algorytmów kryptograficznych](../code-quality/ca5350-do-not-use-weak-cryptographic-algorithms.md)|Słabe algorytmy szyfrowania i funkcje wyznaczania wartości skrótu są obecnie używane z wielu powodów, ale nie powinny być używane do zagwarantowania poufności lub integralności chronionych danych.        Ta reguła jest wyzwalana po znalezieniu w kodzie algorytmów TripleDES, SHA1 lub RIPEMD160.|
|[CA5351: Nie używaj uszkodzonych algorytmów kryptograficznych](../code-quality/ca5351-do-not-use-broken-cryptographic-algorithms.md)|Uszkodzone algorytmy kryptograficzne nie są uważane za bezpieczne, a ich użycie nie powinno być zdecydowanie zalecane. Ta reguła jest wyzwalana, gdy odnajdzie algorytm wyznaczania wartości skrótu MD5 lub algorytmy szyfrowania DES lub RC2 w kodzie.|
