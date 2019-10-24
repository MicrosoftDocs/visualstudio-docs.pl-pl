---
title: Funkcja SccInitialize | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccInitialize
helpviewer_keywords:
- SccInitialize function
ms.assetid: 5bc0d28b-2c68-4d43-9e51-541506a8f76e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 552ec06a4eabf55872358fc8e5d731e47c1eb6ca
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721186"
---
# <a name="sccinitialize-function"></a>SccInitialize, funkcja
Ta funkcja inicjuje wtyczkę kontroli źródła i zapewnia możliwości i limity zintegrowanego środowiska programistycznego (IDE).

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

podczas Wtyczka do kontroli źródła może umieścić wskaźnik do jego struktury kontekstu w tym miejscu.

 `hWnd`

podczas Uchwyt okna środowiska IDE, który może być używany przez wtyczkę kontroli źródła jako element nadrzędny dla dowolnych okien dialogowych, które zapewnia.

 `lpCallerName`

podczas Nazwa programu wywołującego wtyczkę kontroli źródła.

 `lpSccName`

[in. out] Bufor, w którym wtyczka do kontroli źródła umieszcza własną nazwę (nie przekracza `SCC_NAME_LEN`).

 `lpSccCaps`

określoną Zwraca flagi możliwości wtyczki kontroli źródła.

 `lpAuxPathLabel`

[in. out] Bufor, w którym Wtyczka kontroli źródła umieszcza ciąg, który opisuje parametr `lpAuxProjPath` zwracany przez [SccOpenProject](../extensibility/sccopenproject-function.md) i [SccGetProjPath](../extensibility/sccgetprojpath-function.md) (nie przekracza `SCC_AUXLABEL_LEN`).

 `pnCheckoutCommentLen`

określoną Zwraca maksymalną dopuszczalną długość komentarza do wyewidencjonowania.

 `pnCommentLen`

określoną Zwraca maksymalną dopuszczalną długość dla innych komentarzy.

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła tej funkcji powinna zwracać jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Inicjalizacja kontroli źródła zakończyła się pomyślnie.|
|SCC_E_INITIALIZEFAILED|Nie można zainicjować systemu.|
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać określonej operacji.|
|SCC_E_NONSPECFICERROR|Nieokreślony błąd; System kontroli źródła nie został zainicjowany.|

## <a name="remarks"></a>Uwagi
 IDE wywołuje tę funkcję, gdy najpierw ładuje wtyczkę kontroli źródła. Umożliwia IDE przekazywanie pewnych informacji, takich jak nazwa obiektu wywołującego, do wtyczki. IDE pobiera również pewne informacje, takie jak maksymalna dozwolona długość komentarzy i możliwości wtyczki.

 @No__t_0 wskazuje na `NULL` wskaźnik. Wtyczka do kontroli źródła może przydzielić strukturę do własnego użytku i przechowywać wskaźnik do tej struktury w `ppvContext`. IDE przekaże ten wskaźnik do każdej innej funkcji interfejsu API VSSCI, dzięki czemu wtyczka będzie mieć dostęp do informacji kontekstowych bez konieczności używania magazynu globalnego i obsługi wielu wystąpień wtyczki. Ta struktura powinna zostać cofnięta alokacja, gdy zostanie wywołana [SccUninitialize](../extensibility/sccuninitialize-function.md) .

 Parametry `lpCallerName` i `lpSccName` umożliwiają środowisko IDE i wtyczkę kontroli źródła do wymiany nazw. Nazwy te mogą być używane po prostu do rozróżnienia między wieloma wystąpieniami lub mogą być wyświetlane w menu lub oknach dialogowych.

 @No__t_0 parametr jest ciągiem używanym jako komentarz do identyfikacji pomocniczej ścieżki projektu przechowywanej w pliku rozwiązania i przekazaną do wtyczki kontroli źródła w wywołaniu [SccOpenProject](../extensibility/sccopenproject-function.md). [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] używa ciągu "Project SourceSafe:"; inne wtyczki kontroli źródła nie mogą korzystać z tego konkretnego ciągu.

 @No__t_0 parametr udostępnia wtyczkę kontroli źródła w miejscu do przechowywania bitflags wskazujących możliwości wtyczki. (Aby zapoznać się z pełną listą możliwości bitflags, zobacz [flagi możliwości](../extensibility/capability-flags.md)). Na przykład, jeśli wtyczka planuje pisać wyniki do funkcji wywołania zwrotnego dostarczonej przez wywołującego, wtyczka ustawi funkcję bit SCC_CAP_TEXTOUT. Spowoduje to nasygnalizowanie środowiska IDE w celu utworzenia okna dla wyników kontroli wersji.

## <a name="see-also"></a>Zobacz także
- [Funkcje interfejsu API wtyczki kontroli źródła ](../extensibility/source-control-plug-in-api-functions.md)
- [SccUninitialize](../extensibility/sccuninitialize-function.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [Flagi możliwości](../extensibility/capability-flags.md)