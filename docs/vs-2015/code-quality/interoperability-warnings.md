---
title: Ostrzeżenia dotyczące współdziałania | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.Interoperabilityrules
helpviewer_keywords:
- managed code analysis warnings, interoperability warnings
- interoperability warnings
- warnings, interoperability
ms.assetid: 95de6eb3-40c4-4063-9f59-25cb70e3b2b3
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: fd914a65ff23b05130cb0c36162bb96a3d30aa52
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656501"
---
# <a name="interoperability-warnings"></a>Współdziałanie — Ostrzeżenia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ostrzeżenia dotyczące współdziałania obsługują interakcję z klientami modelu COM.

## <a name="in-this-section"></a>W tej sekcji

|Reguła|Opis|
|----------|-----------------|
|[CA1400: punkty wejścia P/Invoke powinny istnieć](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)|Metoda publiczna lub chroniona jest oznaczona za pomocą atrybutu System.Runtime.InteropServices.DllImportAttribute. Nie można zlokalizować biblioteki niezarządzanej lub dopasować metody do funkcji w bibliotece.|
|[CA1401: P/Invoke nie powinna być widoczna](../code-quality/ca1401-p-invokes-should-not-be-visible.md)|Metoda publiczna lub chroniona w typie publicznym ma atrybut System.Runtime.InteropServices.DllImportAttribute (również zaimplementowany przez słowo kluczowe Declare w Visual Basic). Takie metody nie powinny być udostępniane.|
|[CA1402: Unikaj przeciążeń w interfejsach widocznych dla modelu COM](../code-quality/ca1402-avoid-overloads-in-com-visible-interfaces.md)|Gdy przeciążone metody są udostępniane klientom COM, tylko pierwsze przeciążenie metody zachowuje swoją nazwę. Kolejne przeciążenia są jednoznacznie nazywane przez dołączenie do nazwy znaku podkreślenia (_) i liczby całkowitej, która odpowiada kolejności deklaracji przeciążeń.|
|[CA1403: Typy z automatycznym układem nie powinny być widoczne dla modelu COM](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|Typ wartości widoczny dla modelu COM jest oznaczony za pomocą atrybutu System. Runtime. InteropServices. StructLayoutAttribute o wartości LayoutKind. Auto. Układ tych typów może się zmieniać między wersjami programu [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , co spowoduje przerwanie klientów com, którzy oczekują określonego układu.|
|[CA1404: Wywołaj metodę GetLastError bezpośrednio po elemencie P/Invoke](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|Wykonano wywołanie metody Marshal. metodę GetLastWin32Error lub równoważnej [!INCLUDE[TLA2#tla_win32](../includes/tla2sharptla-win32-md.md)] funkcji GetLastError, a bezpośrednio poprzednie wywołanie nie jest metodą wywołania platformy.|
|[CA1405: Typy podstawowe typów widocznych dla modelu COM powinny być widoczne dla modelu COM](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|Typ widoczny dla modelu COM pochodzi od typu, który nie jest widoczny dla modelu COM.|
|[CA1406: Unikaj używania argumentów typu Int64 w klientach w języku Visual Basic 6](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)|Klienci Visual Basic 6 COM nie mogą uzyskać dostępu do 64-bitowych liczb całkowitych.|
|[CA1407: Unikaj statycznych składowych w typach widocznych dla modelu COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)|Model COM nie obsługuje metod statycznych.|
|[CA1408: Nie używaj wartości AutoDual elementu ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)|Typy, które korzystają z podwójnych interfejsów, umożliwiają klientom powiązanie z określonym interfejsem. Wszelkie zmiany w przyszłej wersji układu typu lub wszelkich typów podstawowych spowodują przerwanie klientów COM powiązanych z interfejsem. Domyślnie jeśli atrybut ClassInterfaceAttribute nie jest określony, używany jest interfejs służący tylko do wysłania.|
|[CA1409: Typy widoczne dla modelu COM powinny mieć możliwość utworzenia](../code-quality/ca1409-com-visible-types-should-be-creatable.md)|Typ odwołania, który jest specjalnie oznaczony jako widoczny dla modelu COM, zawiera publiczny konstruktor sparametryzowany, ale nie zawiera publicznego domyślnego (bezparametrowego) konstruktora. Klienci COM nie mogą stworzyć typu bez publicznego konstruktora domyślnego.|
|[CA1410: Metody rejestracji modelu COM powinny mieć swoje odpowiedniki](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|Typ deklaruje metodę, która jest oznaczona przy użyciu <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> atrybutu, ale nie deklaruje metody, która jest oznaczona za pomocą <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> atrybutu lub odwrotnie.|
|[CA1411: Metody rejestracji modelu COM nie powinny być widoczne](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)|Metoda oznaczona przy użyciu atrybutu System. Runtime. InteropServices. ComRegisterFunctionAttribute lub atrybutu System. Runtime. InteropServices. ComUnregisterFunctionAttribute jest widoczna na zewnątrz.|
|[CA1412: Oznacz interfejsy ComSource atrybutem IDispatch](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)|Typ jest oznaczony za pomocą atrybutu System.Runtime.InteropServices.ComSourceInterfacesAttribute i co najmniej jeden z określonych interfejsów nie jest oznaczony za pomocą atrybutu System.Runtime.InteropServices.InterfaceTypeAttribute ustawionego na ComInterfaceType.InterfaceIsIDispatch.|
|[CA1413: Unikaj niepublicznych pól w typach wartości widocznych w modelu COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)|Pola niepubliczne wystąpień typów wartości widocznych dla modelu COM są widoczne dla klientów COM. Przejrzyj zawartość pól pod kątem informacji, które nie powinny być eksponowane lub będą mieć niezamierzone efekty dla projektu lub zabezpieczeń.|
|[CA1414: Oznacz argumenty logiczne P/Invoke za pomocą elementu MarshalAs](../code-quality/ca1414-mark-boolean-p-invoke-arguments-with-marshalas.md)|Typ danych Boolean ma wiele reprezentacji w kodzie niezarządzanym.|
|[CA1415: Zadeklaruj prawidłowo element P/Invoke](../code-quality/ca1415-declare-p-invokes-correctly.md)|Ta reguła poszukuje deklaracji metody wywołania platformy, które [!INCLUDE[TLA2#tla_win32](../includes/tla2sharptla-win32-md.md)] są funkcjami docelowymi, które mają wskaźnik do nakładający się parametrów struktury, a odpowiadający mu parametr zarządzany nie jest wskaźnikiem do <xref:System.Threading.NativeOverlapped?displayProperty=fullName> struktury.|
