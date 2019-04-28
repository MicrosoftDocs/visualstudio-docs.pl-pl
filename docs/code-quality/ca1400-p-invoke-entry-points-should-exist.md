---
title: 'CA1400: Punkty wejścia P-Invoke powinny istnieć'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1400
- PInvokeEntryPointsShouldExist
helpviewer_keywords:
- PInvokeEntryPointsShouldExist
- CA1400
ms.assetid: 1d64e470-7b2f-4cca-8fb0-ac92829e6332
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2374e3c1aa79414bfa39ea97abeec7e8e44d2c36
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62797374"
---
# <a name="ca1400-pinvoke-entry-points-should-exist"></a>CA1400: Punkty wejścia P/Invoke powinny istnieć

|||
|-|-|
|TypeName|PInvokeEntryPointsShouldExist|
|CheckId|CA1400|
|Kategoria|Microsoft.Interoperability|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Metoda publiczna lub chroniona jest oznaczona atrybutem <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. Nie można zlokalizować biblioteki niezarządzanej lub dopasować metody do funkcji w bibliotece. Jeśli zasada nie można odnaleźć nazwy metody, dokładnie tak, jak zostało to określone, szuka ANSI lub wersjami szerokich znaków metody dodając nazwę metody z '' lub 'W'. Jeśli nie zostanie znalezione dopasowanie, reguła próbuje zlokalizować funkcję przy użyciu formatu nazwy __stdcall (_MyMethod@12, gdzie 12 reprezentuje długość argumentów). Jeśli nie zostanie znalezione dopasowanie, a nazwę metody zaczyna się od '#', reguła szuka funkcji jako odwołanie porządkowej zamiast nazwy odwołania.

## <a name="rule-description"></a>Opis reguły
 Sprawdzanie kompilacji nie jest dostępna dla upewnij się, że metody, które są oznaczone <xref:System.Runtime.InteropServices.DllImportAttribute> znajdują się w przywoływanych niezarządzaną biblioteką DLL. Jeśli żadna funkcja, która ma określoną nazwę znajduje się w bibliotece lub argumenty do metody nie są zgodne z argumentów funkcji, środowisko uruchomieniowe języka wspólnego generuje wyjątek.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, popraw metody, która ma <xref:System.Runtime.InteropServices.DllImportAttribute> atrybutu. Upewnij się, że biblioteki niezarządzanej istnieje i znajduje się w tym samym katalogu co zestaw, który zawiera metodę. Biblioteka jest obecny i prawidłowo przywoływany, sprawdź, czy nazwa metody, zwracany typ i podpisu argumentu odpowiadają funkcji biblioteki.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły, gdy biblioteką niezarządzaną znajduje się w tym samym katalogu co zestaw zarządzany, który odwołuje się do niej. Może być bezpiecznie Pomijaj ostrzeżeń dla tej reguły, w przypadku, gdy biblioteką niezarządzaną nie można zlokalizować.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje typ, który narusza regułę. Brak funkcji o nazwie `DoSomethingUnmanaged` występuje w kernel32.dll.

 [!code-csharp[FxCop.Interoperability.DLLExists#1](../code-quality/codesnippet/CSharp/ca1400-p-invoke-entry-points-should-exist_1.cs)]

## <a name="see-also"></a>Zobacz także
 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>