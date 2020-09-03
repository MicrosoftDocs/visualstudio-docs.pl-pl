---
title: Ostrzeżenia dotyczące kryptografii
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: d96723ea-a293-488d-b9db-adb437e50cdd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 78923dfd2873b53790421cde3fe01f024e267202
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75587705"
---
# <a name="cryptography-warnings"></a>Ostrzeżenia dotyczące kryptografii
Ostrzeżenia kryptografii obsługują bezpieczniejsze biblioteki i aplikacje poprzez poprawne użycie kryptografii. Ostrzeżenia te pomagają zapobiec usterkom w zabezpieczeniach w programie. Przyczynę wyłączenia któregokolwiek z tych ostrzeżeń należy wyraźnie oznaczyć w kodzie i poinformować o tym osobę odpowiedzialną za bezpieczeństwo w projekcie.

|Reguła|Opis|
|----------|-----------------|
|[CA5350: Nie używaj słabych algorytmów kryptograficznych](../code-quality/ca5350.md)|Słabe algorytmy szyfrowania i funkcje wyznaczania wartości skrótu są obecnie używane z wielu powodów, ale nie powinny być używane do zagwarantowania poufności lub integralności chronionych danych.        Ta reguła jest wyzwalana po znalezieniu w kodzie algorytmów TripleDES, SHA1 lub RIPEMD160.|
|[CA5351: Nie używaj uszkodzonych algorytmów kryptograficznych](../code-quality/ca5351.md)|Uszkodzone algorytmy kryptograficzne nie są uważane za bezpieczne, a ich użycie nie powinno być zdecydowanie zalecane. Ta reguła jest wyzwalana, gdy odnajdzie algorytm wyznaczania wartości skrótu MD5 lub algorytmy szyfrowania DES lub RC2 w kodzie.|
