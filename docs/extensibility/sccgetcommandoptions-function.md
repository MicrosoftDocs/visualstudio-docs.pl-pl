---
title: Funkcja SccGetCommandOptions | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetCommandOptions
helpviewer_keywords:
- SccGetCommandOptions function
ms.assetid: bbe4aa4e-b4b0-403e-b7a0-5dd6eb24e5a9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: eeefa26422476ca40e782df3ff35eee9d429a149
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700830"
---
# <a name="sccgetcommandoptions-function"></a>Funkcja SccGetCommandOptions,
Ta funkcja monituje użytkownika o zaawansowane opcje dla danego polecenia.

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

[w] Struktura kontekstu wtyczki formantu źródła.

 Hwnd

[w] Dojście do okna IDE, którego wtyczka formantu źródła może używać jako element nadrzędny dla wszystkich okien dialogowych, które udostępnia.

 Icommand

[w] Polecenie, dla którego są wymagane opcje zaawansowane (zobacz [Kod polecenia](../extensibility/command-code-enumerator.md) dla możliwych wartości).

 ppvOptions (ppvOptions)

[w] Struktura opcji (może `NULL`być również ).

## <a name="return-value"></a>Wartość zwracana
 Oczekuje się, że implementacja wtyczki kontroli źródła tej funkcji zwróci jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Powodzenie.|
|SCC_I_ADV_SUPPORT|Wtyczka kontroli źródła obsługuje zaawansowane opcje dla polecenia.|
|SCC_I_OPERATIONCANCELED|Użytkownik anulował okno dialogowe **Opcje** wtyczki kontroli źródła.|
|SCC_E_OPTNOTSUPPORTED|Wtyczka kontroli źródła nie obsługuje tej operacji.|
|SCC_E_ISCHECKEDOUT|Nie można wykonać tej operacji na pliku, który jest obecnie wyewidencjonowany.|
|SCC_E_ACCESSFAILURE|Wystąpił problem z dostępem do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub rywalizacją. Zaleca się ponowną próbę.|
|SCC_E_NONSPECIFICERROR|Niespecyficzna awaria.|

## <a name="remarks"></a>Uwagi
 IDE wywołuje tę funkcję po `ppvOptions` = `NULL` raz pierwszy, aby ustalić, czy wtyczka kontroli źródła obsługuje funkcję zaawansowanych opcji dla określonego polecenia. Jeśli wtyczka obsługuje tę funkcję dla tego polecenia, IDE wywołuje tę funkcję ponownie, gdy użytkownik żąda zaawansowanych opcji (zwykle zaimplementowanych jako `NULL` przycisk **Zaawansowane** w oknie dialogowym) i dostarcza wskaźnik nie null dla `ppvOptions` tego wskazuje wskaźnik. Wtyczka przechowuje wszystkie zaawansowane opcje określone przez użytkownika w strukturze prywatnej `ppvOptions`i zwraca wskaźnik do tej struktury w . Ta struktura jest następnie przekazywana do wszystkich innych funkcji interfejsu API dodatku `SccGetCommandOptions` Source Control Plug-in, które muszą o niej wiedzieć, w tym kolejnych wywołań funkcji.

 Przykład może pomóc wyjaśnić tę sytuację.

 Użytkownik wybiera polecenie **Pobierz,** a w ide wyświetla okno dialogowe **Pobierz.** IDE wywołuje `SccGetCommandOptions` funkcję `iCommand` z `SCC_COMMAND_GET` ustawioną `NULL`na . `ppvOptions` Jest to interpretowane przez wtyczkę kontroli źródła jako pytanie" Czy masz jakieś zaawansowane opcje dla tego polecenia?" Jeśli wtyczka powróci, `SCC_I_ADV_SUPPORT`w oknie dialogowym **Pobierz** zostanie wyświetlony przycisk **Zaawansowane.**

 Gdy użytkownik po raz pierwszy kliknie przycisk `SccGetCommandOptions` **Zaawansowane,** IDE ponownie wywołuje`NULL``ppvOptions` funkcję, `NULL` tym razem z non-, który wskazuje na wskaźnik. Wtyczka wyświetla własne okno dialogowe **Pobierz opcje,** monituje użytkownika o informacje, umieszcza te informacje we `ppvOptions`własnej strukturze i zwraca wskaźnik do tej struktury w programie .

 Jeśli użytkownik ponownie kliknie **przycisk Zaawansowane** w tym `SccGetCommandOptions` samym oknie `ppvOptions`dialogowym, IDE wywołuje funkcję ponownie bez zmiany , tak aby struktura została przekazana z powrotem do wtyczki. Dzięki temu wtyczka może ponownie zainicjować okno dialogowe do wartości, które użytkownik wcześniej ustawił. Wtyczka modyfikuje strukturę w miejscu przed powrotem.

 Na koniec, gdy użytkownik kliknie **OK** w oknie dialogowym **Pobierz** IDE, IDE wywołuje `ppvOptions` [SccGet](../extensibility/sccget-function.md), przekazując strukturę zwróconą, która zawiera opcje zaawansowane.

> [!NOTE]
> Polecenie `SCC_COMMAND_OPTIONS` jest używane, gdy IDE wyświetla okno dialogowe **Opcje,** które umożliwia użytkownikowi ustawianie preferencji, które sterują działaniem integracji. Jeśli wtyczka formantu źródła chce podać własne okno dialogowe preferencji, może wyświetlać je za pomocą przycisku **Zaawansowane** w oknie dialogowym preferencje IDE. Wtyczka jest wyłącznie odpowiedzialna za uzyskanie i utrwalanie tych informacji; IDE nie używa go lub modyfikować go.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki sterowania źródłem](../extensibility/source-control-plug-in-api-functions.md)
- [Kod polecenia](../extensibility/command-code-enumerator.md)
