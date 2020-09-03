---
title: Funkcja SccCheckin | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccCheckin
helpviewer_keywords:
- SccCheckin function
ms.assetid: e3f26ac2-6163-42e1-a764-22cfea5a3bc6
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d8a5a91a0300f256b66970403a3431edf0fe757e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189533"
---
# <a name="scccheckin-function"></a>SccCheckin, funkcja
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ta funkcja sprawdza wcześniej wyewidencjonowane pliki do systemu kontroli źródła, przechowując zmiany i tworząc nową wersję. Ta funkcja jest wywoływana z liczbą i tablicą nazw plików do zaewidencjonowania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
SCCRTN SccCheckin (  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPSTR*    lpFileNames,  
   LPCSTR    lpComment,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pvContext  
 podczas Struktura kontekstu wtyczki kontroli źródła.  
  
 Właściwość  
 podczas Dojście do okna IDE, które może być używane przez wtyczkę SCC jako element nadrzędny dla dowolnych okien dialogowych, które zapewnia.  
  
 nFiles  
 podczas Liczba plików wybranych do zaewidencjonowania.  
  
 lpFileNames  
 podczas Tablica w pełni kwalifikowanych nazw ścieżek lokalnych dla plików do zaewidencjonowania.  
  
 lpComment  
 podczas Komentarz, który ma zostać zastosowany do każdego z wybranych plików, które są zaewidencjonowane. Jest to `NULL` Jeśli wtyczka do kontroli źródła powinna monitować o komentarz.  
  
 fOptions  
 podczas Flagi poleceń, 0 lub `SCC_KEEP_CHECKEDOUT` .  
  
 pvOptions  
 podczas Opcje dotyczące wtyczki SCC.  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczki kontroli źródła tej funkcji powinna zwracać jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Pomyślnie zaewidencjonowano pliki.|  
|SCC_E_FILENOTCONTROLLED|Wybrany plik nie znajduje się pod kontrolą kodu źródłowego.|  
|SCC_E_ACCESSFAILURE|Wystąpił problem z uzyskaniem dostępu do systemu kontroli źródła prawdopodobnie z powodu problemów z siecią lub rywalizacją. Zalecana jest ponowna próba.|  
|SCC_E_NONSPECIFICERROR|Nieokreślony błąd. Plik nie został zaewidencjonowany.|  
|SCC_E_NOTCHECKEDOUT|Użytkownik nie wyewidencjonuje pliku, więc nie może go zaewidencjonować.|  
|SCC_E_CHECKINCONFLICT|Nie można wykonać zaewidencjonowania, ponieważ:<br /><br /> — Inny użytkownik zaewidencjonuje się z wyprzedzeniem i `bAutoReconcile` miał wartość false.<br /><br /> -lub-<br /><br /> -Nie można wykonać automatycznego scalania (na przykład wtedy, gdy pliki są binarne).|  
|SCC_E_VERIFYMERGE|Plik został scalony z autoscalaniem, ale nie został zaewidencjonowany w toku weryfikacji przez użytkownika.|  
|SCC_E_FIXMERGE|Plik został automatycznie scalony, ale nie został zaewidencjonowany z powodu konfliktu scalania, który należy ręcznie rozwiązać.|  
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|  
|SCC_I_OPERATIONCANCELED|Operacja została anulowana przed ukończeniem.|  
|SCC_I_RELOADFILE|Plik lub projekt musi zostać ponownie załadowany.|  
|SCC_E_FILENOTEXIST|Nie znaleziono pliku lokalnego.|  
  
## <a name="remarks"></a>Uwagi  
 Komentarz dotyczy wszystkich plików, które są zaewidencjonowane. Argument komentarza może być `null` ciągiem, w takim przypadku wtyczka do kontroli źródła może monitować użytkownika o podanie ciągu komentarza dla każdego pliku.  
  
 `fOptions`Argument może mieć wartość `SCC_KEEP_CHECKEDOUT` flagi, aby wskazać zamiar użytkownika do sprawdzenia pliku i wyewidencjonować go ponownie.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
