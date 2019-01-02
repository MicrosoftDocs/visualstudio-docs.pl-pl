---
title: 'CA1060: Przenieś P-Invoke do klasy NativeMethods | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- MovePInvokesToNativeMethodsClass
- CA1060
helpviewer_keywords:
- MovePInvokesToNativeMethodsClass
- CA1060
ms.assetid: 06686c8c-6ad3-42f7-a355-cbaefa347cfc
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 019d02b8cd5031148a2902ed3bda54640dcc6587
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53849287"
---
# <a name="ca1060-move-pinvokes-to-nativemethods-class"></a>CA1060: Przenieś P/Invokes do klasy NativeMethods
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MovePInvokesToNativeMethodsClass|
|CheckId|CA1060|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Metoda wykorzystuje platformę wywołania usług dostęp do niezarządzanego kodu i nie jest członkiem jednej z **NativeMethods** klasy.

## <a name="rule-description"></a>Opis reguły
 Metody platform Invocation, takich jak te, które są oznaczone za pomocą <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> atrybutu lub metody, które są zdefiniowane przy użyciu `Declare` — słowo kluczowe w [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], dostęp do kodu niezarządzanego. Metody te powinny być w jednym z następujących klas:

- **NativeMethods** -tej klasy nie pomija przeszukiwań stosu dla niezarządzanego kodu uprawnienia. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> nie może być stosowane do tej klasy.) Ta klasa jest dla metod, które może służyć wszędzie ponieważ przeszukiwania stosu, zostaną wykonane.

- **SafeNativeMethods** -tej klasy pomija przeszukiwań stosu dla niezarządzanego kodu uprawnienia. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> jest stosowany do tej klasy.) Ta klasa jest dla metod, które są bezpieczne dla każdego, kto do wywołania. Obiekty wywołujące tych metod nie są wymagane do przeprowadzenia przeglądu pełne zabezpieczenia, aby upewnić się, że użycie jest bezpieczna, ponieważ metody jest bezpieczna dla każdego obiektu wywołującego.

- **UnsafeNativeMethods** -tej klasy pomija przeszukiwań stosu dla niezarządzanego kodu uprawnienia. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> jest stosowany do tej klasy.) Ta klasa jest dla metod, które mogą być niebezpieczne. Dowolny obiekt wywołujący metody te należy wykonać przegląd pełne zabezpieczenia, aby upewnić się, że użycie jest bezpieczna, ponieważ zostaną wykonane nie stosów.

  Te klasy są deklarowane jako `internal` (`Friend`, w języku Visual Basic) i Zadeklaruj Konstruktor prywatny, aby uniemożliwić Trwa tworzenie nowych wystąpień. Powinny móc wywoływać metody w ramach tych zajęć `static` i `internal` (`Shared` i `Friend` w języku Visual Basic).

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy przenieść metodę do odpowiedniego **NativeMethods** klasy. W przypadku większości aplikacji przenoszenie P/Invokes do nową klasę o nazwie **NativeMethods** jest wystarczająca.

 Jednak jeśli tworzysz biblioteki do użycia w innych aplikacjach, należy rozważyć definiowanie dwóch klas, które są wywoływane **SafeNativeMethods** i **UnsafeNativeMethods**. W ramach tych zajęć przypominają **NativeMethods** klasy; jednak są oznaczone za pomocą specjalnych atrybutu o nazwie **SuppressUnmanagedCodeSecurityAttribute**. Jeśli ten atrybut jest stosowany, środowisko uruchomieniowe wykonuje przeszukiwania pełnego stosu, aby upewnić się, że wszystkie obiekty wywołujące **UnmanagedCode** uprawnień. Środowisko uruchomieniowe zwykle sprawdza, czy to uprawnienie, podczas uruchamiania. Ponieważ nie jest wykonywane sprawdzanie, umożliwia poprawę wydajności wywołania tych metod niezarządzanych, umożliwia ona także kodu, które ma ograniczone uprawnienia do wywołania tych metod.

 Jednakże należy użyć tego atrybutu bardzo ostrożnie. Jeśli wdrażana jest niepoprawnie może mieć poważne konsekwencje dla bezpieczeństwa...

 Aby uzyskać informacje o sposobie implementacji metod, zobacz **NativeMethods** przykład **SafeNativeMethods** przykład i **UnsafeNativeMethods** przykład.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład deklaruje metodę, która narusza tę regułę. Aby naprawić naruszenie, **RemoveDirectory** P/Invoke powinny zostać przeniesione do odpowiedniej klasy, która jest przeznaczona do przechowywania tylko P/Invokes.

 [!code-csharp[FxCop.Design.DllImportNativeMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.DllImportNativeMethods/cs/FxCop.Design.DllImportNativeMethods.cs#1)]
 [!code-vb[FxCop.Design.DllImportNativeMethods#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.DllImportNativeMethods/vb/FxCop.Design.DllImportNativeMethods.vb#1)]

## <a name="nativemethods-example"></a>Przykład NativeMethods

### <a name="description"></a>Opis
 Ponieważ **NativeMethods** klasy nie powinien być oznaczony za pomocą **SuppressUnmanagedCodeSecurityAttribute**, P/Invokes, które są umieszczane w nim będzie wymagać **UnmanagedCode** uprawnienie. Ponieważ większość aplikacje są uruchamiane z komputera lokalnego, a następnie uruchomić, wraz z pełnym zaufaniem, zazwyczaj nie jest to problem. Jednak jeśli tworzysz biblioteki do ponownego wykorzystania, należy rozważyć definiowanie **SafeNativeMethods** lub **UnsafeNativeMethods** klasy.

 W poniższym przykładzie przedstawiono **Interaction.Beep** metodę, która otacza **MessageBeep** funkcji z user32.dll. **MessageBeep** P/Invoke jest umieszczany w **NativeMethods** klasy.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Design.NativeMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethods/cs/FxCop.Design.NativeMethods.cs#1)]
 [!code-vb[FxCop.Design.NativeMethods#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethods/vb/FxCop.Design.NativeMethods.vb#1)]

## <a name="safenativemethods-example"></a>Przykład SafeNativeMethods

### <a name="description"></a>Opis
 Metody P/Invoke, które mogą bezpiecznie łączyć się z dowolnej aplikacji i które nie mają żadnych efektów ubocznych powinien znajdować się w klasie o nazwie **SafeNativeMethods**. Nie masz uprawnień na żądanie i nie trzeba płacić większej uwagi, do której zostaną wywołane.

 W poniższym przykładzie przedstawiono **Environment.TickCount** właściwość, która otacza **GetTickCount** funkcji z modułu kernel32.dll.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Design.NativeMethodsSafe#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsSafe/cs/FxCop.Design.NativeMethodsSafe.cs#1)]
 [!code-vb[FxCop.Design.NativeMethodsSafe#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsSafe/vb/FxCop.Design.NativeMethodsSafe.vb#1)]

## <a name="unsafenativemethods-example"></a>Przykład UnsafeNativeMethods

### <a name="description"></a>Opis
 Metody P/Invoke, który nie można bezpiecznie wywołać i który może spowodować skutki uboczne powinien znajdować się w klasie o nazwie **UnsafeNativeMethods**. Te metody powinny być starannie sprawdzane, aby upewnić się, że ich nie są widoczne dla użytkownika przypadkowo. Reguła [CA2118: Przejrzyj przypadki użycia atrybutu SuppressUnmanagedCodeSecurityAttribute](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md) może w tym pomóc. Alternatywnie metody powinny mieć inny uprawnienia, które jest wymagane zamiast **UnmanagedCode** po ich używają.

 W poniższym przykładzie przedstawiono **Cursor.Hide** metodę, która otacza **wartość** funkcji z user32.dll.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Design.NativeMethodsUnsafe#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsUnsafe/cs/FxCop.Design.NativeMethodsUnsafe.cs#1)]
 [!code-vb[FxCop.Design.NativeMethodsUnsafe#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsUnsafe/vb/FxCop.Design.NativeMethodsUnsafe.vb#1)]

## <a name="see-also"></a>Zobacz też
 [Ostrzeżenia dotyczące projektu](../code-quality/design-warnings.md)
