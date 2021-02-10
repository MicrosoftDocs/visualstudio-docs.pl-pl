---
title: Funkcja SccGetCommandOptions | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetCommandOptions
helpviewer_keywords:
- SccGetCommandOptions function
ms.assetid: bbe4aa4e-b4b0-403e-b7a0-5dd6eb24e5a9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3b1f465e6709932cd89794c5c0558d608fadd2a8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965203"
---
# <a name="sccgetcommandoptions-function"></a>SccGetCommandOptions, funkcja
Ta funkcja poprosi użytkownika o opcje zaawansowane dla danego polecenia.

## <a name="syntax"></a>Składnia

```cpp
SCCRTN SccGetCommandOptions(
   LPVOID pvContext,
   HWND hWnd,
   enum SCCCOMMAND iCommand,
   LPCMDOPTS* ppvOptions
);
```

### <a name="parameters"></a>Parametry
 pvContext

podczas Struktura kontekstu wtyczki kontroli źródła.

 Właściwość

podczas Uchwyt okna środowiska IDE, który może być używany przez wtyczkę kontroli źródła jako element nadrzędny dla dowolnych okien dialogowych, które zapewnia.

 Interfejs ICommand

podczas Polecenie, dla którego zażądano zaawansowanych opcji (zobacz [kod polecenia](../extensibility/command-code-enumerator.md) dla możliwych wartości).

 ppvOptions

podczas Struktura opcji (może również być `NULL` ).

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła tej funkcji powinna zwracać jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Powodzenie.|
|SCC_I_ADV_SUPPORT|Wtyczka do kontroli źródła obsługuje zaawansowane opcje polecenia.|
|SCC_I_OPERATIONCANCELED|Użytkownik anulował okno dialogowe **Opcje** wtyczki kontroli źródła.|
|SCC_E_OPTNOTSUPPORTED|Wtyczka do kontroli źródła nie obsługuje tej operacji.|
|SCC_E_ISCHECKEDOUT|Nie można wykonać tej operacji na pliku, który jest obecnie wyewidencjonowany.|
|SCC_E_ACCESSFAILURE|Wystąpił problem z uzyskaniem dostępu do systemu kontroli źródła prawdopodobnie z powodu problemów z siecią lub rywalizacją. Zalecana jest ponowna próba.|
|SCC_E_NONSPECIFICERROR|Nieokreślony błąd.|

## <a name="remarks"></a>Uwagi
 IDE wywołuje tę funkcję po raz pierwszy w programie, `ppvOptions` = `NULL` Aby określić, czy wtyczka kontroli źródła obsługuje funkcję opcji zaawansowanych dla określonego polecenia. Jeśli wtyczka obsługuje funkcję dla tego polecenia, IDE wywołuje tę funkcję ponownie, gdy użytkownik zażąda opcji zaawansowanych (zazwyczaj zaimplementowanych jako przycisk **Zaawansowany** w oknie dialogowym) i dostarcza wskaźnik o wartości innej niż null dla `ppvOptions` tego punktu `NULL` wskaźnika. Wtyczka przechowuje wszystkie opcje zaawansowane określone przez użytkownika w strukturze prywatnej i zwraca wskaźnik do tej struktury w `ppvOptions` . Ta struktura jest następnie przenoszona do wszystkich innych funkcji interfejsu API dodatku plug-in kontroli źródła, które muszą je znać, łącznie z kolejnymi wywołaniami `SccGetCommandOptions` funkcji.

 Przykład może pomóc w wyjaśnieniu takiej sytuacji.

 Użytkownik wybiera polecenie **Get** , a IDE wyświetla okno dialogowe **pobieranie** . IDE wywołuje `SccGetCommandOptions` funkcję z `iCommand` ustawioną na `SCC_COMMAND_GET` i `ppvOptions` ustawioną na `NULL` . Jest to interpretowane przez wtyczkę kontroli źródła jako pytanie "czy masz jakieś opcje zaawansowane dla tego polecenia?". Jeśli wtyczka jest zwracana `SCC_I_ADV_SUPPORT` , IDE wyświetla przycisk **Zaawansowane** w oknie dialogowym **pobieranie** .

 Gdy użytkownik po raz pierwszy kliknie przycisk **Zaawansowane** , środowisko IDE ponownie wywołuje `SccGetCommandOptions` funkcję, tym razem z `NULL``ppvOptions` niewskazującym `NULL` wskaźnikiem. Wtyczka wyświetla własne okno dialogowe **pobieranie opcji** , wyświetla informacje o użytkowniku, umieszcza je w własnej strukturze i zwraca wskaźnik do tej struktury w `ppvOptions` .

 Jeśli użytkownik kliknie ponownie przycisk **Zaawansowane** w tym samym oknie dialogowym, środowisko IDE ponownie wywołuje `SccGetCommandOptions` funkcję bez zmiany `ppvOptions` , aby struktura została przeniesiona z powrotem do wtyczki. Dzięki temu wtyczka będzie ponownie inicjować okno dialogowe do wartości, które wcześniej zostały ustawione przez użytkownika. Wtyczka modyfikuje strukturę w miejscu przed zwróceniem.

 Na koniec, gdy użytkownik kliknie **OK** w oknie dialogowym **pobieranie** środowiska IDE, IDE wywołuje [SccGet](../extensibility/sccget-function.md), przekazując w ten sposób strukturę, `ppvOptions` która zawiera opcje zaawansowane.

> [!NOTE]
> Polecenie `SCC_COMMAND_OPTIONS` jest używane, gdy środowisko IDE wyświetla okno dialogowe **Opcje** , które pozwala ustawić preferencje, które kontrolują sposób działania integracji. Jeśli wtyczka do kontroli źródła chce zapewnić własne okno dialogowe preferencji, może wyświetlić ją z przycisku **Zaawansowane** w oknie dialogowym Preferencje IDE. Wtyczka jest odpowiedzialna wyłącznie za pobieranie i utrwalanie tych informacji. IDE nie używa go ani nie modyfikuje.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
- [Kod polecenia](../extensibility/command-code-enumerator.md)
