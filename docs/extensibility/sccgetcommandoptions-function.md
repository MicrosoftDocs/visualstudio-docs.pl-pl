---
description: Ta funkcja monituje użytkownika o opcje zaawansowane dla danego polecenia.
title: SccGetCommandOptions, funkcja | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccGetCommandOptions
helpviewer_keywords:
- SccGetCommandOptions function
ms.assetid: bbe4aa4e-b4b0-403e-b7a0-5dd6eb24e5a9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7972d874668649b8bb86adc15008880c5fc4152e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903934"
---
# <a name="sccgetcommandoptions-function"></a>SccGetCommandOptions, funkcja
Ta funkcja monituje użytkownika o opcje zaawansowane dla danego polecenia.

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

[in] Struktura kontekstu wtyczki kontroli źródła.

 Hwnd

[in] Dojście do okna IDE, które wtyczka kontroli źródła może używać jako elementu nadrzędnego dla wszystkich okien dialogowych, które udostępnia.

 Icommand

[in] Polecenie, dla którego żądane są opcje zaawansowane (zobacz [Kod polecenia dla](../extensibility/command-code-enumerator.md) możliwych wartości).

 ppvOptions

[in] Struktura opcji (może być również `NULL` ).

## <a name="return-value"></a>Wartość zwracana
 Oczekuje się, że implementacja wtyczki kontroli źródła dla tej funkcji zwróci jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Powodzenie.|
|SCC_I_ADV_SUPPORT|Wtyczka kontroli źródła obsługuje zaawansowane opcje polecenia.|
|SCC_I_OPERATIONCANCELED|Użytkownik anulował okno dialogowe Opcje wtyczki **kontroli** źródła.|
|SCC_E_OPTNOTSUPPORTED|Wtyczka kontroli źródła nie obsługuje tej operacji.|
|SCC_E_ISCHECKEDOUT|Nie można wykonać tej operacji na pliku, który jest obecnie wyewidencjonowany.|
|SCC_E_ACCESSFAILURE|Występuje problem z dostępem do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub skwedycją. Zaleca się ponawianie próby.|
|SCC_E_NONSPECIFICERROR|Nieokreślona awaria.|

## <a name="remarks"></a>Uwagi
 Ide wywołuje tę funkcję po raz pierwszy za pomocą polecenia , aby określić, czy wtyczka kontroli źródła obsługuje funkcję opcji `ppvOptions` = `NULL` zaawansowanych dla określonego polecenia. Jeśli wtyczka obsługuje funkcję dla tego polecenia, ide wywołuje tę funkcję ponownie, gdy użytkownik  zażąda opcji zaawansowanych (zwykle zaimplementowanych jako przycisk Zaawansowane w oknie dialogowym) i dostarcza wskaźnik o wartości innych niż NULL dla tego `ppvOptions` `NULL` wskaźnika. Wtyczka przechowuje wszystkie opcje zaawansowane określone przez użytkownika w strukturze prywatnej i zwraca wskaźnik do tej struktury w pliku `ppvOptions` . Ta struktura jest następnie przekazywana do wszystkich innych funkcji interfejsu API wtyczki kontroli kodu źródłowego, które muszą się o tym dowiedzieć, w tym do kolejnych wywołań `SccGetCommandOptions` funkcji.

 Przykład może pomóc w wyjaśnieniu tej sytuacji.

 Użytkownik wybierze polecenie **Pobierz,** a w ideu zostanie wyświetlone okno **dialogowe** Pobierz. Ide wywołuje funkcję `SccGetCommandOptions` z `iCommand` ustawioną na i `SCC_COMMAND_GET` `ppvOptions` ustawioną na `NULL` . Jest to interpretowane przez wtyczkę kontroli źródła jako pytanie "Czy masz jakiekolwiek opcje zaawansowane dla tego polecenia?". Jeśli wtyczka zwróci wartość , w oknie dialogowym Get środowiska IDE zostanie wyświetlony przycisk `SCC_I_ADV_SUPPORT` Zaawansowane.  

 Za pierwszym razem, gdy użytkownik kliknie **przycisk** Zaawansowane, ide ponownie wywołuje funkcję , tym razem z wskaźnikiem innym `SccGetCommandOptions` niż `NULL``ppvOptions` `NULL` . Wtyczka wyświetla własne  okno dialogowe Pobierz opcje, monituje użytkownika o informacje, umieszcza te informacje we własnej strukturze i zwraca wskaźnik do tej struktury w `ppvOptions` pliku .

 Jeśli użytkownik kliknie ponownie przycisk **Zaawansowane** w tym samym oknie dialogowym, ide wywołuje funkcję ponownie bez zmiany , aby struktura została przekazana z powrotem `SccGetCommandOptions` do `ppvOptions` wtyczki. Dzięki temu wtyczka może ponownie zainicjować okno dialogowe z wartościami ustawionymi wcześniej przez użytkownika. Wtyczka modyfikuje strukturę przed zwróceniem.

 Na koniec, gdy użytkownik kliknie przycisk  **OK** w oknie dialogowym Pobierz środowiska IDE, idee wywołuje [SccGet](../extensibility/sccget-function.md), przekazując zwróconą strukturę zawierającą `ppvOptions` opcje zaawansowane.

> [!NOTE]
> To polecenie jest używane, gdy w idee jest wyświetlane okno dialogowe Opcje, które umożliwia użytkownikowi ustawianie preferencji, które kontrolują `SCC_COMMAND_OPTIONS` sposób działania  integracji. Jeśli wtyczka kontroli źródła chce podać własne preferencje, może wyświetlić  ją za pomocą przycisku Zaawansowane w oknie dialogowym preferencji środowiska IDE. Wtyczka odpowiada wyłącznie za pobieranie i utrwalanie tych informacji. Ide nie używa go ani nie modyfikuje.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli kodu źródłowego](../extensibility/source-control-plug-in-api-functions.md)
- [Kod polecenia](../extensibility/command-code-enumerator.md)
