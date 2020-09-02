---
title: Funkcja SccAddFromScc | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccAddFromScc
helpviewer_keywords:
- SccAddFromScc function
ms.assetid: 902e764d-200e-46e1-8c42-4da7b037f9a0
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ccf3a25bda14cf98fdba4a58b0032444badc4c4a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64817612"
---
# <a name="sccaddfromscc-function"></a>SccAddFromScc, funkcja
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ta funkcja umożliwia użytkownikowi przeglądanie w poszukiwaniu plików, które znajdują się już w systemie kontroli źródła, a następnie tworzą część tych plików w bieżącym projekcie. Na przykład ta funkcja może pobrać wspólny plik nagłówkowy do bieżącego projektu bez kopiowania pliku. Tablica zwrotna plików, `lplpFileNames` , zawiera listę plików, które użytkownik chce dodać do projektu IDE.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
SCCRTN SccAddFromScc (  
   LPVOID   pvContext,  
   HWND     hWnd,  
   LPLONG   lpnFiles,  
   LPCSTR** lplpFileNames  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pvContext  
 podczas Struktura kontekstu wtyczki kontroli źródła.  
  
 Właściwość  
 podczas Uchwyt okna środowiska IDE, który może być używany przez wtyczkę kontroli źródła jako element nadrzędny dla dowolnych okien dialogowych, które zapewnia.  
  
 lpnFiles  
 [in. out] Bufor dla liczby plików, które są dodawane w. (Jest to `NULL` możliwe, że pamięć wskazywana przez `lplpFileNames` ma zostać wydana. Aby uzyskać szczegółowe informacje, zobacz uwagi.  
  
 lplpFileNames  
 [in. out] Tablica wskaźników do wszystkich nazw plików bez ścieżek katalogów. Ta tablica jest alokowana i zwalniana przez wtyczkę kontroli źródła. Jeśli `lpnFiles` = 1 i `lplpFileNames` nie jest `NULL` , imię w tablicy wskazywane przez `lplpFileNames` zawiera folder docelowy.  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczki kontroli źródła tej funkcji powinna zwracać jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Pliki zostały pomyślnie zlokalizowane i dodane do projektu.|  
|SCC_I_OPERATIONCANCELED|Operacja została anulowana i nie ma żadnego wpływu.|  
|SCC_I_RELOADFILE|Plik lub projekt musi zostać ponownie załadowany.|  
  
## <a name="remarks"></a>Uwagi  
 IDE wywołuje tę funkcję. Jeśli wtyczka do kontroli źródła obsługuje określanie lokalnego folderu docelowego, IDE przekazuje `lpnFiles` = 1 i przekazuje nazwę folderu lokalnego do programu `lplpFileNames` .  
  
 Gdy wywołanie `SccAddFromScc` funkcji zwraca, wtyczka przypisała wartości do `lpnFiles` i `lplpFileNames` , przydzielając pamięć dla tablicy nazw plików w razie potrzeby (należy zauważyć, że ta alokacja zastępuje wskaźnik w `lplpFileNames` ). Wtyczka do kontroli źródła jest odpowiedzialna za umieszczanie wszystkich plików w katalogu użytkownika lub w określonym folderze wyznaczania. IDE dodaje następnie pliki do projektu IDE.  
  
 Na koniec środowisko IDE wywołuje tę funkcję po raz drugi, przekazując polecenie `NULL` do `lpnFiles` . Jest to interpretowane jako sygnał specjalny przez wtyczkę kontroli źródła, aby zwolnić pamięć przydzieloną dla tablicy nazw plików w `lplpFileNames``.`  
  
 `lplpFileNames` jest `char ***` wskaźnikiem. Wtyczka do kontroli źródła umieszcza wskaźnik do tablicy wskaźników do nazw plików, a tym samym przekazuje listę w standardowym sposobie dla tego interfejsu API.  
  
> [!NOTE]
> Początkowe wersje interfejsu API VSSCI nie zapewniają metody wskazywania docelowego projektu dla dodanych plików. Aby to umożliwić, semantyka `lplpFIleNames` parametru została ulepszona w taki sposób, aby była parametrem we/wy, a nie parametrem wyjściowym. Jeśli określony jest tylko jeden plik, oznacza to, że wartość wskazywana przez `lpnFiles` = 1, a następnie pierwszy element `lplpFileNames` zawiera folder docelowy. Aby użyć tej nowej semantyki, IDE wywołuje `SccSetOption` funkcję z `nOption` parametrem ustawionym na `SCC_OPT_SHARESUBPROJ` . Jeśli wtyczka kontroli źródła nie obsługuje semantyki, zwraca `SCC_E_OPTNOTSUPPORTED` . Wykonanie tej czynności spowoduje wyłączenie używania funkcji **Dodaj z kontroli źródła** . Jeśli wtyczka obsługuje funkcję **Dodaj z kontroli źródła** ( `SCC_CAP_ADDFROMSCC` ), wówczas musi obsługiwać nową semantykę i zwracać `SCC_I_SHARESUBPROJOK` .  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)   
 [SccSetOption](../extensibility/sccsetoption-function.md)
