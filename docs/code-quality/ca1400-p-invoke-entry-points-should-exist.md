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
ms.openlocfilehash: b292c58e666c11130fb25f67c234bfd2282fe463
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922257"
---
# <a name="ca1400-pinvoke-entry-points-should-exist"></a>CA1400: Punkty wejścia P/Invoke powinny istnieć

|||
|-|-|
|TypeName|PInvokeEntryPointsShouldExist|
|CheckId|CA1400|
|Kategoria|Microsoft. współdziałanie|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
Metoda publiczna lub chroniona jest oznaczona za <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>pomocą. Nie można zlokalizować biblioteki niezarządzanej lub dopasować metody do funkcji w bibliotece. Jeśli reguła nie może znaleźć nazwy metody dokładnie tak, jak jest określona, szuka wersji ANSI lub znaków dwubajtowych metody przez sufiks nazwy metody z "A" lub "W". Jeśli nie zostanie znalezione dopasowanie, reguła próbuje zlokalizować funkcję przy użyciu formatu nazwy __stdcall (_MyMethod@12, gdzie 12 reprezentuje długość argumentów). Jeśli nie zostanie znalezione dopasowanie, a nazwa metody rozpoczyna się od "#", reguła wyszukuje funkcję jako odwołanie porządkowe, a nie odwołanie do nazwy.

## <a name="rule-description"></a>Opis reguły
Nie jest dostępny żaden test czasu kompilacji, aby upewnić się, że metody oznaczone <xref:System.Runtime.InteropServices.DllImportAttribute> za pomocą znajdują się w odwołującej się do niezarządzanej bibliotece DLL. Jeśli żadna funkcja, która ma określoną nazwę nie znajduje się w bibliotece lub argumenty metody nie są zgodne z argumentami funkcji, środowisko uruchomieniowe języka wspólnego zgłasza wyjątek.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej zasady, należy skorygować metodę, która ma <xref:System.Runtime.InteropServices.DllImportAttribute> atrybut. Upewnij się, że biblioteka niezarządzana istnieje i znajduje się w tym samym katalogu, w którym znajduje się zestaw zawierający metodę. Jeśli biblioteka jest obecna i poprawnie przywoływana, sprawdź, czy nazwa metody, zwracany typ i sygnatura argumentu są zgodne z funkcją biblioteki.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Nie pomijaj ostrzeżenia z tej reguły, jeśli biblioteka niezarządzana znajduje się w tym samym katalogu, co zarządzany zestaw, który odwołuje się do niego. W przypadku, gdy nie można zlokalizować biblioteki niezarządzanej, może być bezpieczne pominięcie ostrzeżenia z tej reguły.

## <a name="example"></a>Przykład
Poniższy przykład pokazuje typ, który narusza regułę. W pliku Kernel32. dll `DoSomethingUnmanaged` nie występuje żadna funkcja o nazwie.

[!code-csharp[FxCop.Interoperability.DLLExists#1](../code-quality/codesnippet/CSharp/ca1400-p-invoke-entry-points-should-exist_1.cs)]

## <a name="see-also"></a>Zobacz także
 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>