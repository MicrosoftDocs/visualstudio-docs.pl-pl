---
title: Funkcja SccCheckin | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccCheckin
helpviewer_keywords:
- SccCheckin function
ms.assetid: e3f26ac2-6163-42e1-a764-22cfea5a3bc6
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 26daf5fcd3ee4ec14b0801c828a6e536a65150d8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51798004"
---
# <a name="scccheckin-function"></a>SccCheckin, funkcja
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ta funkcja sprawdza, czy wcześniej pobranych plików do systemu kontroli źródła, przechowywania zmian i tworzenie nowej wersji. Ta funkcja jest wywoływana z liczbą i tablicę nazw plików do wyewidencjonowania.  
  
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
 [in] Struktura kontekście wtyczki kontroli źródła.  
  
 hWnd  
 [in] Uchwyt okna środowiska IDE, które SCC wtyczki mogą służyć jako element nadrzędny dla wszystkie okna dialogowe, które zawiera.  
  
 Niepowodzeń  
 [in] Liczba plików wybranych do wyewidencjonowania.  
  
 lpFileNames  
 [in] Tablica nazw w pełni kwalifikowaną ścieżką lokalną plików do wyewidencjonowania.  
  
 lpComment  
 [in] Komentarz, które mają być stosowane do każdego z wybranych plików, które zostały zaewidencjonowane. Jest to `NULL` Jeśli wtyczka do kontroli źródła, powinien zostać wyświetlony monit o komentarz.  
  
 fOptions  
 [in] Command flag, albo 0 lub `SCC_KEEP_CHECKEDOUT`.  
  
 pvOptions  
 [in] SCC plug-określonych opcji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczki kontroli źródła tej funkcji powinien zwrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Pliki został pomyślnie zaewidencjonowany.|  
|SCC_E_FILENOTCONTROLLED|Wybrany plik nie jest pod kontrolą kodu źródłowego.|  
|SCC_E_ACCESSFAILURE|Wystąpił problem podczas uzyskiwania dostępu do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub rywalizacji o zasoby. Ponowienie próby jest zalecane.|  
|SCC_E_NONSPECIFICERROR|Wystąpił nieokreślony błąd. Plik nie została zaewidencjonowana.|  
|SCC_E_NOTCHECKEDOUT|Użytkownik nie został wyewidencjonowany pliku, więc nie można sprawdzić.|  
|SCC_E_CHECKINCONFLICT|Nie można wykonać zaewidencjonowania, ponieważ:<br /><br /> -Inny użytkownik zaewidencjonował wyprzedzeniem i `bAutoReconcile` była wartość false.<br /><br /> —lub—<br /><br /> Nie można wykonać automatyczne scalanie, (na przykład w przypadku plików binarnych).|  
|SCC_E_VERIFYMERGE|Plik został scalony automatycznie, ale nie został zaewidencjonowany oczekiwania na weryfikację użytkownika.|  
|SCC_E_FIXMERGE|Plik został scalony automatycznie, ale nie został zaewidencjonowany ze względu na konflikt scalania, które należy ręcznie rozwiązać.|  
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|  
|SCC_I_OPERATIONCANCELED|Operacja została anulowana przed ukończeniem.|  
|SCC_I_RELOADFILE|Pliku lub projektu wymaga ponownego załadowania.|  
|SCC_E_FILENOTEXIST|Nie można odnaleźć pliku lokalnego.|  
  
## <a name="remarks"></a>Uwagi  
 Komentarza ma zastosowanie do wszystkich plików, które zostały zaewidencjonowane. Argument komentarz może być `null` ciągu, w którym to przypadku wtyczka do kontroli źródła może monitować użytkownika o ciąg komentarza dla każdego pliku.  
  
 `fOptions` Wartość może być podany argument `SCC_KEEP_CHECKEDOUT` flagę wskazującą intencji użytkownika Zaewidencjonuj go i ponownie Sprawdź wprowadzone zmiany.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje interfejsu API wtyczki kontroli źródła ](../extensibility/source-control-plug-in-api-functions.md)

