---
title: Współdziałanie — Ostrzeżenia
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.Interoperabilityrules
helpviewer_keywords:
- managed code analysis warnings, interoperability warnings
- interoperability warnings
- warnings, interoperability
ms.assetid: 95de6eb3-40c4-4063-9f59-25cb70e3b2b3
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7a4e8f7bc60704842a8a0e940b336b4bb79093b2
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2019
ms.locfileid: "66745135"
---
# <a name="interoperability-warnings"></a>Współdziałanie — Ostrzeżenia

Ostrzeżenia dotyczące współdziałania obsługują interakcji z klientami COM.

## <a name="in-this-section"></a>W tej sekcji

| Reguła | Opis |
| - | - |
| [CA1400: Powinny istnieć punkty wejścia P/Invoke](../code-quality/ca1400-p-invoke-entry-points-should-exist.md) | Metoda publiczna lub chroniona jest oznaczona za pomocą atrybutu System.Runtime.InteropServices.DllImportAttribute. Nie można zlokalizować biblioteki niezarządzanej lub dopasować metody do funkcji w bibliotece. |
| [CA1401: P/Invokes nie powinny być widoczne](../code-quality/ca1401-p-invokes-should-not-be-visible.md) | Metoda publiczna lub chroniona w typie publicznym ma atrybut System.Runtime.InteropServices.DllImportAttribute (również implementowany przez słowo kluczowe Declare w języku Visual Basic). Takie metody nie powinny być udostępniane. |
| [CA1402: Unikaj przeciążeń w interfejsach widocznych dla modelu COM](../code-quality/ca1402-avoid-overloads-in-com-visible-interfaces.md) | Gdy przeciążone metody są udostępniane klientom COM, tylko pierwsze przeciążenie metody zachowuje swoją nazwę. Kolejne przeciążenia są jednoznacznie nazywane przez dołączenie do nazwy znaku podkreślenia (_) i liczby całkowitej, która odpowiada kolejności deklaracji przeciążeń. |
| [CA1403: Typy automatycznego układu nie powinny być widoczne dla modelu COM](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md) | Typ wartości widocznej dla modelu COM jest oznaczony za pomocą atrybutu System.Runtime.InteropServices.StructLayoutAttribute ustawionego na LayoutKind.Auto. Układ tych typów można zmieniać między wersjami .NET, które spowodują przerwanie klientów COM, które oczekują określonego układu. |
| [CA1404: Wywołaj metodę GetLastError natychmiast po P/Invoke](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md) | Wykonano wywołanie do metody Marshal.GetLastWin32Error lub równoważny [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] funkcję GetLastError, a bezpośrednio poprzedzające wywołanie nie jest to platforma wywołania metody. |
| [CA1405: Typy podstawowe typu widocznego modelu COM powinny być widoczne dla modelu COM](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md) | Typ widoczny dla modelu COM pochodzi od typu, który nie jest widoczny dla modelu COM. |
| [CA1406: Unikaj argumentów Int64 dla klientów w języku Visual Basic 6](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md) | Klienci Visual Basic 6 COM nie może uzyskać dostęp do 64-bitowych liczb całkowitych. |
| [CA1407: Unikaj statycznych elementów członkowskich w typach widocznych dla modelu COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md) | Model COM nie obsługuje metod statycznych. |
| [CA1408: Nie używaj wartości AutoDual elementu ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md) | Typy, które korzystają z podwójnych interfejsów, umożliwiają klientom powiązanie z określonym interfejsem. Wszelkie zmiany w przyszłej wersji układu typu lub wszelkich typów podstawowych spowodują przerwanie klientów COM powiązanych z interfejsem. Domyślnie jeśli atrybut ClassInterfaceAttribute nie jest określony, używany jest interfejs służący tylko do wysłania. |
| [CA1409: Typy widoczne dla modelu COM powinny mieć możliwość utworzenia](../code-quality/ca1409-com-visible-types-should-be-creatable.md) | Typ odwołania, który jest specjalnie oznaczony jako widoczny dla modelu COM, zawiera publiczny konstruktor sparametryzowany, ale nie zawiera publicznego domyślnego (bezparametrowego) konstruktora. Klienci COM nie mogą stworzyć typu bez publicznego konstruktora domyślnego. |
| [CA1410: Metody rejestracji modelu COM powinny być dopasowane](../code-quality/ca1410-com-registration-methods-should-be-matched.md) | Typ deklaruje metodę, która jest oznaczona za pomocą <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> atrybutu, ale nie deklaruje metodę, która jest oznaczona za pomocą <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> atrybut, lub na odwrót. |
| [CA1411: Metody rejestracji modelu COM nie powinny być widoczne](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md) | Metoda, która jest oznaczona za pomocą atrybutu System.Runtime.InteropServices.ComRegisterFunctionAttribute lub atrybutu System.Runtime.InteropServices.ComUnregisterFunctionAttribute jest widoczna na zewnątrz. |
| [CA1412: Oznacz interfejsy ComSource jako IDispatch](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md) | Typ jest oznaczony za pomocą atrybutu System.Runtime.InteropServices.ComSourceInterfacesAttribute i co najmniej jeden z określonych interfejsów nie jest oznaczony za pomocą atrybutu System.Runtime.InteropServices.InterfaceTypeAttribute ustawionego na ComInterfaceType.InterfaceIsIDispatch. |
| [CA1413: Unikaj pól niepublicznych w typach wartości widocznych dla modelu COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md) | Pola niepubliczne wystąpień typów wartości widocznych dla modelu COM są widoczne dla klientów COM. Przejrzyj zawartość pól pod kątem informacji, które nie powinny być eksponowane lub będą mieć niezamierzone efekty dla projektu lub zabezpieczeń. |
| [CA1414: Oznacz logiczne argumenty P/Invoke za pomocą atrybutu MarshalAs](../code-quality/ca1414-mark-boolean-p-invoke-arguments-with-marshalas.md) | Typ danych Boolean ma wiele reprezentacji w kodzie niezarządzanym. |
| [CA1415: Poprawnie Zadeklaruj P/Invokes](../code-quality/ca1415-declare-p-invokes-correctly.md) | Ta zasada będzie wyglądać dla deklaracji metod wywołania platformy, których platformą docelową [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] parametru struktury funkcji, które mają wskaźnik do OVERLAPPED, a odpowiadający parametr zarządzalny nie jest wskaźnikiem do <xref:System.Threading.NativeOverlapped?displayProperty=fullName> struktury. |