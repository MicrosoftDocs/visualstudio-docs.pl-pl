---
title: Funkcja SccPopulateList | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccPopulateList
helpviewer_keywords:
- SccPopulateList function
ms.assetid: 7416e781-c571-4a7f-8af3-a089ce8be662
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b41cea5b06022764e2f05ddd32f1ed476934f691
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53887779"
---
# <a name="sccpopulatelist-function"></a>SccPopulateList, funkcja
Ta funkcja aktualizuje listę pliki dla polecenia kontroli konkretnego źródła i dostarcza stan kontroli źródła na wszystkie pliki danego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
SCCRTN SccPopulateList (  
   LPVOID          pvContext,  
   enum SCCCOMMAND nCommand,  
   LONG            nFiles,  
   LPCSTR*         lpFileNames,  
   POPLISTFUNC     pfnPopulate,  
   LPVOID          pvCallerData,  
   LPLONG          lpStatus,  
   LONG            fOptions  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pvContext  
 [in] Struktura kontekście wtyczki kontroli źródła.  
  
 Npolecenie  
 [in] Polecenie kontroli źródła, które zostaną zastosowane do wszystkich plików w `lpFileNames` tablicy (zobacz [kod polecenia](../extensibility/command-code-enumerator.md) listę poleceń możliwe).  
  
 Niepowodzeń  
 [in] Liczba plików w `lpFileNames` tablicy.  
  
 lpFileNames  
 [in] Tablica nazw plików, wiadomo, że środowisko IDE.  
  
 pfnPopulate  
 [in] IDE funkcji wywołania zwrotnego wywoływana w celu dodawania i usuwania plików (zobacz [POPLISTFUNC](../extensibility/poplistfunc.md) Aby uzyskać szczegółowe informacje).  
  
 pvCallerData  
 [in] Niezmieniona wartość, która zostanie przekazany do funkcji wywołania zwrotnego.  
  
 lpStatus  
 [out w] Tablica wtyczka do kontroli źródła do zwrócenia flagi stanu dla każdego pliku.  
  
 fOptions  
 [in] Polecenie flagi (zobacz sekcję "PopulateList flag" [flagi bitowe używane przez określone polecenia](../extensibility/bitflags-used-by-specific-commands.md) Aby uzyskać szczegółowe informacje).  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczki kontroli źródła tej funkcji powinien zwrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Powodzenie.|  
|SCC_E_NONSPECIFICERROR|Wystąpił nieokreślony błąd.|  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja sprawdza, czy lista plików dla ich bieżący stan. Używa ona `pfnPopulate` funkcji wywołania zwrotnego powiadomić obiekt wywołujący, gdy plik jest niezgodny z kryteriami, które dla `nCommand`. Na przykład, jeśli polecenie jest `SCC_COMMAND_CHECKIN` pliku na liście nie został wyewidencjonowany, a następnie wywołania zwrotnego służy do informowania obiektu wywołującego. Od czasu do czasu wtyczka do kontroli źródła może się okazać innych plików, które mogą być częścią polecenia, a następnie dodać je. Dzięki temu, na przykład użytkownika języka Visual Basic, aby wyewidencjonować pliku .bmp, który jest używany przez własny projekt, ale nie ma w pliku projektu języka Visual Basic. Użytkownik wybierze **uzyskać** polecenie w IDE. IDE spowoduje wyświetlenie listy wszystkich plików, które uważa, że użytkownik może otrzymać, ale przed listy jest wyświetlany, `SccPopulateList` funkcja jest wywoływana, aby upewnić się, listy, które mają być wyświetlane są aktualne.  
  
## <a name="example"></a>Przykład  
 IDE kompiluje listę plików, które uważa, że użytkownik może otrzymać. Przed wyświetleniem tej listy, wywołuje `SccPopulateList` funkcji, co daje możliwość wtyczka do kontroli źródła Dodawanie i usuwanie plików z listy. Wtyczka modyfikuje listę przez wywołanie funkcji wywołania zwrotnego danego (zobacz [POPLISTFUNC](../extensibility/poplistfunc.md) Aby uzyskać więcej informacji).  
  
 Wtyczka w dalszym ciągu wywołania `pfnPopulate` funkcji, która dodaje i usuwa pliki, dopóki nie zostało zakończone, a następnie zwraca z `SccPopulateList` funkcji. IDE może następnie wyświetlić jego listy. `lpStatus` Tablicy reprezentuje wszystkie pliki w oryginalnej listy, które są przekazywane w IDE. Użyj wtyczki wypełnia stan wszystkich tych plików dodatkowo na rzecz uczynienia funkcji wywołania zwrotnego.  
  
> [!NOTE]
>  Wtyczka do kontroli źródła zawsze może po prostu natychmiastowy powrót z tej funkcji, pozostawiając na liście, ponieważ jest. Jeśli wtyczka implementuje tę funkcję, może on wskazywać na to, ustawiając `SCC_CAP_POPULATELIST` flag bitowych możliwości, w pierwszym wywołaniu [SccInitialize](../extensibility/sccinitialize-function.md). Domyślnie wtyczka powinna zawsze zakładaj, że wszystkie elementy przekazywany czy pliki. Jednak jeśli ustawia IDE `SCC_PL_DIR` znacznik w `fOptions` parametru, wszystkie elementy przekazywany mają być traktowane jako katalogów. Wtyczkę należy dodać wszystkie pliki, które należy w katalogach. IDE nigdy nie będą przekazywane w kombinacji plików i katalogów.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)   
 [Flagi bitowe używane przez określone polecenia](../extensibility/bitflags-used-by-specific-commands.md)   
 [Kod polecenia](../extensibility/command-code-enumerator.md)