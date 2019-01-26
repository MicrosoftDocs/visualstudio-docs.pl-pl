---
title: SccGetCommandOptions Function | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetCommandOptions
helpviewer_keywords:
- SccGetCommandOptions function
ms.assetid: bbe4aa4e-b4b0-403e-b7a0-5dd6eb24e5a9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d4ba76a398bd3d5976ba0b2edb1356194f17014c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55005443"
---
# <a name="sccgetcommandoptions-function"></a>SccGetCommandOptions function
Ta funkcja monituje użytkownika o zaawansowane opcje dla podanego polecenia.  
  
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
 [in] Struktura kontekście wtyczki kontroli źródła.  
  
 hWnd  
 [in] Uchwyt okna środowiska IDE, które wtyczka do kontroli źródła można użyć jako element nadrzędny dla wszystkie okna dialogowe, które zawiera.  
  
 Interfejs iCommand  
 [in] Polecenie, dla których wymagane są opcje zaawansowane (zobacz [polecenia kodu](../extensibility/command-code-enumerator.md) uzyskać odpowiednie wartości).  
  
 ppvOptions  
 [in] Struktura opcji (może być również `NULL`).  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczki kontroli źródła tej funkcji powinien zwrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Powodzenie.|  
|SCC_I_ADV_SUPPORT|Wtyczka do kontroli źródła obsługuje zaawansowane opcje polecenia.|  
|SCC_I_OPERATIONCANCELED|Użytkownik anulował źródła kontrolki wtyczki do firmy **opcje** okno dialogowe.|  
|SCC_E_OPTNOTSUPPORTED|Wtyczka do kontroli źródła nie obsługuje tej operacji.|  
|SCC_E_ISCHECKEDOUT|Nie można wykonać tej operacji na pliku, który jest obecnie wyewidencjonowany.|  
|SCC_E_ACCESSFAILURE|Wystąpił problem podczas uzyskiwania dostępu do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub rywalizacji o zasoby. Ponowienie próby jest zalecane.|  
|SCC_E_NONSPECIFICERROR|Wystąpił nieokreślony błąd.|  
  
## <a name="remarks"></a>Uwagi  
 IDE wywołuje tę funkcję, po raz pierwszy przy użyciu `ppvOptions` = `NULL` do określenia, czy wtyczka do kontroli źródła obsługuje funkcję opcji zaawansowanych dla określonego polecenia. Jeśli wtyczka obsługuje tę funkcję dla tego polecenia, IDE wywołuje tę funkcję ponownie gdy użytkownik zażąda opcje zaawansowane (zwykle implementowane jako **zaawansowane** przycisku w oknie dialogowym) i dostarcza wskaźnik ZEROWY dla `ppvOptions` wskazującej `NULL` wskaźnika. Wtyczka przechowuje opcje zaawansowane określone przez użytkownika w strukturze prywatne i zwraca wskaźnik do tej struktury w `ppvOptions`. Ta struktura jest następnie przekazywany do wszystkich innych funkcji interfejsu API wtyczki kontroli źródła, które musisz wiedzieć o tym, w tym kolejnych wywołań `SccGetCommandOptions` funkcji.  
  
 Przykładem może pomóc wyjaśnić tę sytuację.  
  
 Użytkownik wybierze **uzyskać** polecenia i środowisko IDE Wyświetla **uzyskać** okno dialogowe. Wywołania środowiska IDE `SccGetCommandOptions` funkcją `iCommand` równa `SCC_COMMAND_GET` i `ppvOptions` równa `NULL`. To jest interpretowane przez wtyczka do kontroli źródła jako pytanie, "Masz wszystkie zaawansowane opcje dla tego polecenia?" Jeśli wtyczka zwraca `SCC_I_ADV_SUPPORT`, środowisko IDE Wyświetla **zaawansowane** znajdujący się w jego **uzyskać** okno dialogowe.  
  
 Użytkownik klika polecenie po raz pierwszy **zaawansowane** przycisk, IDE ponownie wywołuje `SccGetCommandOptions` funkcji, tym razem z systemem innym niż`NULL``ppvOptions` wskazującego na `NULL` wskaźnika. Wtyczka wyświetla własną **uzyskać opcje** okno dialogowe monituje użytkownika o informacje, umieszcza w własną strukturę i zwraca wskaźnik do tej struktury w `ppvOptions`.  
  
 Jeśli użytkownik kliknie **zaawansowane** ponownie w tym samym oknie dialogowym IDE wywołuje `SccGetCommandOptions` funkcja ponownie bez konieczności zmieniania `ppvOptions`, dzięki czemu struktury jest przekazywana do wtyczki. Dzięki temu dodatek plug-in ponownie zainicjować okno dialogowe jego wartości, które użytkownik ma ustawione wcześniej. Wtyczka modyfikuje struktury w miejscu przed zwróceniem.  
  
 Ponadto, kiedy użytkownik kliknie **OK** w środowisku IDE **uzyskać** okno dialogowe, wywołania IDE [SccGet](../extensibility/sccget-function.md), przekazywanie struktury zwracane w `ppvOptions` zawierający Opcje zaawansowane.  
  
> [!NOTE]
>  Polecenie `SCC_COMMAND_OPTIONS` jest używany, gdy środowisko IDE Wyświetla **opcje** okno dialogowe, w którym użytkownik może ustawić preferencje, które kontrolują, jak działa integracja. Jeśli wtyczka do kontroli źródła chce, aby podać własne okno dialogowe Preferencje, może on zawierać go z **zaawansowane** przycisku w okno dialogowe preferencji środowiska IDE. Wtyczka jest wyłączną odpowiedzialność za uzyskanie i przechowywanie te informacje; IDE nie używać go lub go zmodyfikować.  
  
## <a name="see-also"></a>Zobacz także  
 [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)   
 [Kod polecenia](../extensibility/command-code-enumerator.md)