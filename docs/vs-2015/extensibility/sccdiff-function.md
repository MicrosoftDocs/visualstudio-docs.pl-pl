---
title: Funkcja SccDiff | Dokumentacja firmy Microsoft
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
- SccDiff
helpviewer_keywords:
- SccDiff function
ms.assetid: d49bc8c5-f631-4153-9d3c-feb3564da305
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ed4ca5cefa45f041e4285b00d7a2d9682e6565a0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51795755"
---
# <a name="sccdiff-function"></a>SccDiff, funkcja
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ta funkcja zawiera (lub opcjonalnie tylko sprawdza, czy) system kontroli różnice między bieżącego pliku (na dysku lokalnym) i jego ostatniej wersji w źródle.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
SCCRTN SccDiff(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LPCSTR    lpFileName,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pvContext  
 [in] Struktura kontekście wtyczki kontroli źródła.  
  
 hWnd  
 [in] Uchwyt okna środowiska IDE, które wtyczka do kontroli źródła można użyć jako element nadrzędny dla wszystkie okna dialogowe, które zawiera.  
  
 lpFileName  
 [in] Nazwa pliku, dla którego żądana jest różnica.  
  
 fOptions  
 [in] Polecenie flagi. Aby uzyskać szczegółowe informacje, zobacz uwagi.  
  
 pvOptions  
 [in] Opcje plug-określonych kontroli źródła.  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczki kontroli źródła tej funkcji powinien zwrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Działającej wersji kopii i serwera są identyczne.|  
|SCC_I_FILESDIFFERS|Kopia robocza różni się od wersji pod kontrolą źródła.|  
|SCC_I_RELOADFILE|Pliku lub projektu wymaga ponownego załadowania.|  
|SCC_E_FILENOTCONTROLLED|Plik nie jest pod kontrolą źródła.|  
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|  
|SCC_E_ACCESSFAILURE|Wystąpił problem podczas uzyskiwania dostępu do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub rywalizacji o zasoby. Ponowienie próby jest zalecane.|  
|SCC_E_NONSPECIFICERROR|Nieokreślony błąd; Nie można uzyskać pliku różnica.|  
|SCC_E_FILENOTEXIST|Nie można odnaleźć pliku lokalnego.|  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja służy do dwóch różnych celów. Domyślnie Wyświetla listę zmian w pliku. Wtyczka do kontroli źródła zostanie otwarty w osobnym oknie w formacie, niezależnie od zdecyduje, aby wyświetlić różnice między użytkownika pliku na dysku i najnowszą wersję pliku objętego kontrolą źródła.  
  
 Alternatywnie IDE może wystarczy określić, czy plik został zmieniony. Na przykład IDE może być konieczne do ustalenia, czy można bezpiecznie wyewidencjonować plik bez informowania o tym użytkownika. W takim przypadku IDE przekazuje `SCC_DIFF_CONTENTS` flagi. Wtyczka do kontroli źródła należy sprawdzić plik na dysku, bajt po bajcie, plik pod kontrolą źródła i zwraca wartość wskazującą, czy dwa pliki różnią się bez wyświetlania niczego do użytkownika.  
  
 Jak zoptymalizować wydajność, wtyczka do kontroli źródła może użyć zamiast na podstawie sumy kontrolnej lub sygnatury czasowej zamiast porównania bajt po bajcie, wymagane przez `SCC_DIFF_CONTENTS`: te rodzaje porównania są oczywiście szybsze, ale mniej niezawodne. Nie wszystkie systemów kontroli źródła może obsługiwać te metody porównania alternatywny, a wtyczka może być konieczne wracać do porównania zawartości. Wtyczek kontroli wszystkie źródła muszą co najmniej obsługiwać porównania zawartości.  
  
> [!NOTE]
>  Flagi szybkiego różnica wzajemnie się wykluczają. Jest on prawidłowy do przekazania bez flag, ale nie jest prawidłową jednocześnie przekazać więcej niż jeden. `SCC_DIFF_QUICK_DIFF`, która jest maską, który łączy wszystkie flagi mogą służyć do testowania, ale nigdy nie powinien być przekazywany jako parametr.  
  
|`fOption`|Znaczenie|  
|---------------|-------------|  
|SCC_DIFF_IGNORECASE|Porównanie bez uwzględniania wielkości liter (mogą być używane do różnica szybkiego lub visual).|  
|SCC_DIFF_IGNORESPACE|Ignoruje biały znak (mogą być używane do różnica szybkiego lub visual).|  
|SCC_DIFF_QD_CONTENTS|Dyskretnie porównuje plik bajt po bajcie.|  
|SCC_DIFF_QD_CHECKSUM|Porównuje dyskretnie pliku za pośrednictwem sumy kontrolnej, jeśli są obsługiwane. Jeśli nie jest obsługiwane, powraca do porównania z zawartością.|  
|SCC_DIFF_QD_TIME|Porównuje dyskretnie pliku za pośrednictwem jego sygnatura czasowa, jeśli są obsługiwane. Jeśli nie jest obsługiwane, powraca do porównania z zawartością.|  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje interfejsu API wtyczki kontroli źródła ](../extensibility/source-control-plug-in-api-functions.md)

