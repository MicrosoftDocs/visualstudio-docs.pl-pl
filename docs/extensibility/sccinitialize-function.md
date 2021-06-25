---
description: Ta funkcja inicjuje wtyczkę kontroli źródła i zapewnia możliwości i limity zintegrowanego środowiska projektowego (IDE).
title: SccInitialize, funkcja | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccInitialize
helpviewer_keywords:
- SccInitialize function
ms.assetid: 5bc0d28b-2c68-4d43-9e51-541506a8f76e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 633e8909febd758df455a9375f735a93e3407c77
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902530"
---
# <a name="sccinitialize-function"></a>SccInitialize, funkcja
Ta funkcja inicjuje wtyczkę kontroli źródła i zapewnia możliwości i limity zintegrowanego środowiska projektowego (IDE).

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

[in] Wtyczka kontroli źródła może w tym miejscu umieścić wskaźnik do jego struktury kontekstu.

 `hWnd`

[in] Dojście do okna IDE, które wtyczka kontroli źródła może używać jako elementu nadrzędnego dla wszystkich okien dialogowych, które udostępnia.

 `lpCallerName`

[in] Nazwa programu wywołującego wtyczkę kontroli źródła.

 `lpSccName`

[in, out] Bufor, w którym wtyczka kontroli kodu źródłowego umieszcza własną nazwę (nie może przekraczać `SCC_NAME_LEN` wartości ).

 `lpSccCaps`

[out] Zwraca flagi możliwości wtyczki kontroli źródła.

 `lpAuxPathLabel`

[in, out] Bufor, w którym wtyczka kontroli źródła umieszcza ciąg opisujący parametr zwracany przez `lpAuxProjPath` [SccOpenProject](../extensibility/sccopenproject-function.md) i [SccGetProjPath](../extensibility/sccgetprojpath-function.md) (nie do przekroczenia `SCC_AUXLABEL_LEN` ).

 `pnCheckoutCommentLen`

[out] Zwraca maksymalną dozwoloną długość komentarza do finalizacji zakupu.

 `pnCommentLen`

[out] Zwraca maksymalną dozwoloną długość dla innych komentarzy.

## <a name="return-value"></a>Wartość zwracana
 Oczekuje się, że implementacja wtyczki kontroli źródła dla tej funkcji zwróci jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Inicjowanie kontroli źródła zakończyło się pomyślnie.|
|SCC_E_INITIALIZEFAILED|Nie można zainicjować systemu.|
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać określonej operacji.|
|SCC_E_NONSPECFICERROR|Nieokreślona awaria; system kontroli źródła nie został zainicjowany.|

## <a name="remarks"></a>Uwagi
 Ide wywołuje tę funkcję podczas pierwszego ładowania wtyczki kontroli źródła. Dzięki temu idee IDE mogą przekazywać pewne informacje, takie jak nazwa wywołującego, do wtyczki. Ide pobiera również pewne informacje, takie jak maksymalna dozwolona długość komentarzy i możliwości wtyczki.

 Wskazuje `ppvContext` `NULL` wskaźnik. Wtyczka kontroli źródła może przydzielić strukturę do własnego użytku i przechowywać wskaźnik do tej struktury w pliku `ppvContext` . Ide przekaże ten wskaźnik do każdej innej funkcji interfejsu API VSSCI, umożliwiając wtyczce dostęp do informacji o kontekście bez konieczności korzystania z magazynu globalnego i obsługi wielu wystąpień wtyczki. Ta struktura powinna być cofana po [wywołaniu SccUninitialize.](../extensibility/sccuninitialize-function.md)

 Parametry `lpCallerName` i umożliwiają programowi IDE i wtyczce kontroli źródła wymianę `lpSccName` nazw. Nazwy te mogą być używane po prostu do rozróżniania wielu wystąpień lub w rzeczywistości mogą pojawiać się w menu lub oknach dialogowych.

 Parametr jest ciągiem używanym jako komentarz do identyfikowania pomocniczej ścieżki projektu, która jest przechowywana w pliku rozwiązania i przekazywana do wtyczki kontroli źródła w wywołaniu `lpAuxPathLabel` [do projektu SccOpenProject](../extensibility/sccopenproject-function.md). [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] używa ciągu "SourceSafe Project:"; inne wtyczki kontroli kodu źródłowego nie powinny używać tego konkretnego ciągu.

 Parametr udostępnia wtyczkę kontroli źródła w miejscu do przechowywania `lpSccCaps` bitflags wskazujących możliwości wtyczki. (Aby uzyskać pełną listę bitflags możliwości, zobacz [Flagi możliwości](../extensibility/capability-flags.md)). Jeśli na przykład wtyczka planuje zapis wyników w funkcji wywołania zwrotnego dostarczonej przez wywołującego, wtyczka ustawi bit możliwości SCC_CAP_TEXTOUT. Zasygnalizuje to ideom utworzenie okna z wynikami kontroli wersji.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
- [SccUninitialize](../extensibility/sccuninitialize-function.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [Flagi możliwości](../extensibility/capability-flags.md)
