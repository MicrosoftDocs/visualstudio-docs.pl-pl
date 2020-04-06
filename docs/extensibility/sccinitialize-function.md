---
title: Funkcja SccInitialize | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccInitialize
helpviewer_keywords:
- SccInitialize function
ms.assetid: 5bc0d28b-2c68-4d43-9e51-541506a8f76e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 661e0a24fa1d222079fd5ee728c5f42a5386c75b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700631"
---
# <a name="sccinitialize-function"></a>SccInitialize, funkcja
Ta funkcja inicjuje wtyczkę kontroli źródła i zapewnia możliwości i ograniczenia zintegrowanego środowiska programistycznego (IDE).

## <a name="syntax"></a>Składnia

```cpp
SCCRTN SccInitialize (
   LPVOID* ppvContext,
   HWND    hWnd,
   LPCSTR  lpCallerName,
   LPSTR   lpSccName,
   LPLONG  lpSccCaps,
   LPSTR   lpAuxPathLabel,
   LPLONG  pnCheckoutCommentLen,
   LPLONG  pnCommentLen
);
```

#### <a name="parameters"></a>Parametry
 `ppvContext`

[w] Wtyczka kontroli źródła można umieścić wskaźnik do jego struktury kontekstu w tym miejscu.

 `hWnd`

[w] Dojście do okna IDE, którego wtyczka formantu źródła może używać jako element nadrzędny dla wszystkich okien dialogowych, które udostępnia.

 `lpCallerName`

[w] Nazwa programu wywołującego wtyczkę kontroli źródła.

 `lpSccName`

[w, na zewnątrz] Bufor, w którym wtyczka kontroli źródła umieszcza własną `SCC_NAME_LEN`nazwę (nie przekracza).

 `lpSccCaps`

[na zewnątrz] Zwraca flagi wtyczki funkcji wtyczki kontroli źródła.

 `lpAuxPathLabel`

[w, na zewnątrz] Bufor, w którym wtyczka formantu źródła `lpAuxProjPath` umieszcza ciąg opisujący parametr zwrócony przez [SccOpenProject](../extensibility/sccopenproject-function.md) `SCC_AUXLABEL_LEN`i [SccGetProjPath](../extensibility/sccgetprojpath-function.md) (nie przekracza).

 `pnCheckoutCommentLen`

[na zewnątrz] Zwraca maksymalną dopuszczalną długość komentarza do wyewidencjonowania.

 `pnCommentLen`

[na zewnątrz] Zwraca maksymalną dopuszczalną długość dla innych komentarzy.

## <a name="return-value"></a>Wartość zwracana
 Oczekuje się, że implementacja wtyczki kontroli źródła tej funkcji zwróci jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Inicjowanie kontroli źródła powiodło się.|
|SCC_E_INITIALIZEFAILED|Nie można zainicjować systemu.|
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać określonej operacji.|
|SCC_E_NONSPECFICERROR|Niespecyficzna awaria; system kontroli źródła nie został zainicjowany.|

## <a name="remarks"></a>Uwagi
 IDE wywołuje tę funkcję, gdy po raz pierwszy ładuje wtyczkę kontroli źródła. Umożliwia IDE przekazać pewne informacje, takie jak nazwa wywołującego, do wtyczki. IDE pobiera również pewne informacje, takie jak maksymalna dopuszczalna długość komentarzy i możliwości wtyczki.

 Wskazuje `ppvContext` na `NULL` wskaźnik. Wtyczka formantu źródła może przydzielić strukturę do własnego użytku `ppvContext`i zapisać wskaźnik do tej struktury w . IDE przekaże ten wskaźnik do każdej innej funkcji interfejsu API VSSCI, dzięki czemu dodatek umożliwia dostęp do informacji kontekstowych bez uciekania się do magazynu globalnego i obsługuje wiele wystąpień dodatku plug-in. Ta struktura powinna być cofnięta alokacji, gdy [SccUninitialize](../extensibility/sccuninitialize-function.md) jest wywoływana.

 Parametry `lpCallerName` `lpSccName` i umożliwiają IDE i wtyczki formantu źródła do wymiany nazw. Nazwy te mogą być używane po prostu do rozróżniania między wieloma wystąpieniami lub mogą faktycznie pojawić się w menu lub oknach dialogowych.

 Parametr `lpAuxPathLabel` jest ciągiem używanym jako komentarz do identyfikowania pomocniczej ścieżki projektu, która jest przechowywana w pliku rozwiązania i przekazywana do wtyczki kontroli źródła w wywołaniu [SccOpenProject](../extensibility/sccopenproject-function.md). [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)]używa ciągu "SourceSafe Project:"; inne wtyczki kontroli źródła powinny powstrzymać się od używania tego konkretnego ciągu.

 Parametr `lpSccCaps` zapewnia wtyczkę sterującą źródłem w miejscu przechowywania bitflags wskazujących możliwości wtyczki. (Aby uzyskać pełną listę bitflags możliwości, zobacz [Flagi możliwości](../extensibility/capability-flags.md)). Na przykład jeśli dodatek typu plug-in planuje zapisywać wyniki w funkcji wywołania zwrotnego dostarczonej przez wywołującego, dodatek umożliwia ustawienie bitu SCC_CAP_TEXTOUT. Oznaczałoby to IDE, aby utworzyć okno dla wyników kontroli wersji.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
- [SccUninitialize](../extensibility/sccuninitialize-function.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [Flagi możliwości](../extensibility/capability-flags.md)
