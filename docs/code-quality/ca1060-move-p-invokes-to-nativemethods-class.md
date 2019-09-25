---
title: 'CA1060: Przenieś metody P-Invoke do klasy NativeMethods'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MovePInvokesToNativeMethodsClass
- CA1060
helpviewer_keywords:
- MovePInvokesToNativeMethodsClass
- CA1060
ms.assetid: 06686c8c-6ad3-42f7-a355-cbaefa347cfc
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: cfa705654a5cc4122e5ee554fe050722d7883970
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235481"
---
# <a name="ca1060-move-pinvokes-to-nativemethods-class"></a>CA1060: Przenieś metody P/Invoke do klasy NativeMethods

|||
|-|-|
|TypeName|MovePInvokesToNativeMethodsClass|
|CheckId|CA1060|
|Kategoria|Microsoft.Design|
|Zmiana podziału|Kluczowa|

## <a name="cause"></a>Przyczyna

Metoda używa usług wywołania platformy w celu uzyskania dostępu do kodu niezarządzanego i nie jest elementem członkowskim jednej z klas **NativeMethods** .

## <a name="rule-description"></a>Opis reguły

Metody wywołania platformy, takie jak te, które są oznaczone przy użyciu <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> atrybutu lub metod, które są zdefiniowane za `Declare` pomocą słowa kluczowego w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], uzyskują dostęp do niezarządzanego kodu. Metody te powinny znajdować się w jednej z następujących klas:

- **NativeMethods** — Ta klasa nie pomija przechodzenia stosu dla niezarządzanego kodu. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> nie może być zastosowany do tej klasy). Ta klasa jest dla metod, które mogą być używane w dowolnym miejscu, ponieważ zostanie wykonane przeszukiwanie stosu.

- **SafeNativeMethods** — Ta klasa pomija przeszukiwania stosu dla niezarządzanego kodu. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> jest zastosowany do tej klasy). Ta klasa jest dla metod, które są bezpieczne dla każdego do wywołania. Osoby wywołujące te metody nie są wymagane do przeprowadzenia pełnego przeglądu zabezpieczeń, aby upewnić się, że użycie jest bezpieczne, ponieważ metody są nieszkodliwe dla każdego obiektu wywołującego.

- **UnsafeNativeMethods** — Ta klasa pomija przeszukiwania stosu dla niezarządzanego kodu. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> jest zastosowany do tej klasy). Ta klasa jest dla metod, które są potencjalnie niebezpieczne. Każdy obiekt wywołujący te metody musi wykonać pełny przegląd zabezpieczeń, aby upewnić się, że użycie jest bezpieczne, ponieważ nie zostanie wykonane żadne przeszukiwanie stosu.

Klasy te są zadeklarowane `internal` jako`Friend`(, w Visual Basic) i deklarują Konstruktor prywatny, aby zapobiec tworzeniu nowych wystąpień. Metody w tych klasach powinny mieć `static` wartość `internal` i`Shared` ( `Friend` i w Visual Basic).

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej reguły, Przenieś metodę do odpowiedniej klasy **NativeMethods** . W przypadku większości aplikacji przeniesienie P/Invoke do nowej klasy o nazwie **NativeMethods** jest wystarczające.

Jeśli jednak tworzysz biblioteki do użycia w innych aplikacjach, należy rozważyć zdefiniowanie dwóch innych klas o nazwie **SafeNativeMethods** i **UnsafeNativeMethods**. Klasy te przypominają klasę **NativeMethods** ; są one jednak oznaczone przy użyciu specjalnego atrybutu o nazwie **SuppressUnmanagedCodeSecurityAttribute**. Gdy ten atrybut jest stosowany, środowisko uruchomieniowe nie wykonuje pełnego sprawdzenia stosu, aby upewnić się, że wszyscy wywołujący mają uprawnienie **UnmanagedCode** . Środowisko uruchomieniowe zwykle sprawdza dla tego uprawnienia podczas uruchamiania. Ponieważ sprawdzenie nie jest wykonywane, może znacznie poprawić wydajność wywołań tych metod niezarządzanych, a także kod, który ma ograniczone uprawnienia do wywoływania tych metod.

Tego atrybutu należy jednak używać bardzo ostrożnie. Jeśli jest zaimplementowany nieprawidłowo, może to mieć poważne konsekwencje dla bezpieczeństwa.

Aby uzyskać informacje na temat sposobu implementacji metod, zobacz przykład **NativeMethods** , **SafeNativeMethods** example i **UnsafeNativeMethods** .

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
Poniższy przykład deklaruje metodę, która narusza tę regułę. Aby poprawić naruszenie, **RemoveDirectory** p/Invoke należy przenieść do odpowiedniej klasy, która jest przeznaczona do przechowywania tylko P/Invoke.

[!code-vb[FxCop.Design.DllImportNativeMethods#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_1.vb)]
[!code-csharp[FxCop.Design.DllImportNativeMethods#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_1.cs)]

## <a name="nativemethods-example"></a>Przykład NativeMethods

### <a name="description"></a>Opis
Ponieważ Klasa **NativeMethods** nie powinna być oznaczona przy użyciu **SuppressUnmanagedCodeSecurityAttribute**, P/Invoke, które są umieszczane, będzie wymagały uprawnienia **UnmanagedCode** . Ponieważ większość aplikacji jest uruchamiana z komputera lokalnego i działa z pełnym zaufaniem, zazwyczaj nie jest to problem. Jeśli jednak tworzysz biblioteki wielokrotnego użytku, należy rozważyć zdefiniowanie klasy **SafeNativeMethods** lub **UnsafeNativeMethods** .

Poniższy przykład przedstawia sposób **interakcji. dźwięk** , który otacza funkcję **MessageBeep** z User32. dll. **MessageBeep** P/Invoke jest umieszczana w klasie **NativeMethods** .

### <a name="code"></a>Kod
[!code-csharp[FxCop.Design.NativeMethods#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_2.cs)]
[!code-vb[FxCop.Design.NativeMethods#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_2.vb)]

## <a name="safenativemethods-example"></a>Przykład SafeNativeMethods

### <a name="description"></a>Opis
Metody P/Invoke, które mogą być bezpiecznie uwidocznione dla dowolnej aplikacji i które nie mają żadnych efektów ubocznych, powinny być umieszczane w klasie o nazwie **SafeNativeMethods**. Nie musisz zażądać uprawnień i nie musisz zwracać uwagi do lokalizacji, z której są wywoływane.

W poniższym przykładzie przedstawiono Właściwość **Environment.** nieruchomości, która otacza funkcję **GetTickCount** z pliku Kernel32. dll.

### <a name="code"></a>Kod
[!code-vb[FxCop.Design.NativeMethodsSafe#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_3.vb)]
[!code-csharp[FxCop.Design.NativeMethodsSafe#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_3.cs)]

## <a name="unsafenativemethods-example"></a>Przykład UnsafeNativeMethods

### <a name="description"></a>Opis
Metody P/Invoke, które nie mogą być bezpiecznie wywoływane i mogą spowodować, że efekty uboczne powinny zostać umieszczone w klasie o nazwie **UnsafeNativeMethods**. Metody te powinny być ściśle sprawdzone, aby upewnić się, że nie są narażone na użytkownika przypadkowo. Reguła [CA2118: Przejrzyj SuppressUnmanagedCodeSecurityAttribute użycie](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md) może Ci pomóc. Alternatywnie metody powinny mieć inne uprawnienia, które są żądane, zamiast **UnmanagedCode** , gdy ich używają.

Poniższy przykład przedstawia **kursor. Ukryj** metodę, która otacza funkcję **ShowCursor** z User32. dll.

### <a name="code"></a>Kod
[!code-vb[FxCop.Design.NativeMethodsUnsafe#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_4.vb)]
[!code-csharp[FxCop.Design.NativeMethodsUnsafe#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_4.cs)]

## <a name="see-also"></a>Zobacz także

- [Ostrzeżenia dotyczące projektu](../code-quality/design-warnings.md)