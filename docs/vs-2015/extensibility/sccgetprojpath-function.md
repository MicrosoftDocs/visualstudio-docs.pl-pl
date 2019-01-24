---
title: SccGetProjPath Function | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccGetProjPath
helpviewer_keywords:
- SccGetProjPath function
ms.assetid: 1079847e-d45f-4cb8-9d92-1e01ce5d08f6
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 053d8ff8f7e75224b05b1a722ba1bce03cd53a59
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54765278"
---
# <a name="sccgetprojpath-function"></a>SccGetProjPath, funkcja
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ta funkcja monituje użytkownika o ścieżkę projektu, który jest ciągiem, który ma znaczenie tylko do wtyczka do kontroli źródła. Jest ona wywoływana, gdy użytkownik jest:  
  
-   Tworzenie nowego projektu  
  
-   Dodawanie istniejącego projektu do kontroli wersji  
  
-   Próby znalezienia istniejący projekt kontroli wersji  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
SCCRTN SccGetProjPath (  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPSTR  lpUser,  
   LPSTR  lpProjName,  
   LPSTR  lpLocalPath,  
   LPSTR  lpAuxProjPath,  
   BOOL   bAllowChangePath,  
   LPBOOL pbNew  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pvContext  
 [in] Struktura kontekście wtyczki kontroli źródła.  
  
 hWnd  
 [in] Uchwyt okna środowiska IDE, które wtyczka do kontroli źródła można użyć jako element nadrzędny dla wszystkie okna dialogowe, które zawiera.  
  
 lpUser  
 [out w] Nazwa użytkownika (nie przekraczając liczby SCC_USER_SIZE, w tym terminator o wartości NULL)  
  
 lpProjName  
 [out w] Nazwa projektu środowiska IDE, obszar roboczy projektu lub pliku reguł programu make (nie przekraczając liczby SCC_PRJPATH_SIZE, w tym terminator o wartości NULL).  
  
 lpLocalPath  
 [out w] Ścieżka roboczego projektu. Jeśli `bAllowChangePath` jest `TRUE`, wtyczka do kontroli źródła można zmodyfikować te parametry (nie przekraczając liczby _MAX_PATH, w tym terminator o wartości null).  
  
 lpAuxProjPath  
 [out w] Bufor dla ścieżki zwrócone projektu (nie przekraczając liczby SCC_PRJPATH_SIZE, w tym terminator o wartości NULL).  
  
 bAllowChangePath  
 [in] Jeśli jest to `TRUE`, wtyczka do kontroli źródła można monitować o i modyfikować `lpLocalPath` ciągu.  
  
 pbNew  
 [out w] Wartość zostaną dodane w wskazuje, czy chcesz utworzyć nowy projekt. Wartość zwracana oznacza sukces tworzenia projektu:  
  
|przychodzące|Interpretacja|  
|--------------|--------------------|  
|WARTOŚĆ TRUE|Użytkownik może utworzyć nowy projekt.|  
|FAŁSZ|Użytkownik nie może utworzyć nowy projekt.|  
  
|Wychodzące|Interpretacja|  
|--------------|--------------------|  
|WARTOŚĆ TRUE|Utworzono nowy projekt.|  
|FAŁSZ|Istniejący projekt został wybrany.|  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczki kontroli źródła tej funkcji powinien zwrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Projekt został pomyślnie utworzony lub pobrać.|  
|SCC_I_OPERATIONCANCELED|Operacja została anulowana.|  
|SCC_E_ACCESSFAILURE|Wystąpił problem podczas uzyskiwania dostępu do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub rywalizacji o zasoby.|  
|SCC_E_CONNECTIONFAILURE|Wystąpił problem podczas próby nawiązania połączenia z systemu kontroli źródła.|  
|SCC_E_NONSPECIFICERROR|Wystąpił nieokreślony błąd.|  
  
## <a name="remarks"></a>Uwagi  
 Celem tej funkcji jest środowisko IDE uzyskać parametry `lpProjName` i `lpAuxProjPath`. Po wtyczka do kontroli źródła monituje użytkownika o te informacje, przekazuje te dwa ciągi do środowiska IDE. Środowisko IDE będzie się powtarzać te ciągi w pliku rozwiązania i przekazuje je do [SccOpenProject](../extensibility/sccopenproject-function.md) zawsze, gdy użytkownik otworzy ten projekt. Te ciągi włączyć dodatek typu plug-in do śledzenia informacji związanych z projektem.  
  
 Po wywołaniu funkcji `lpAuxProjPath` jest ustawiony na pusty ciąg. `lProjName` może być pusty, lub może ona zawierać nazwę projektu środowiska IDE, wtyczka do kontroli źródła może używać lub zignorować. Funkcja zwróci wynik pomyślnie, wtyczka zwraca dwa ciągi odpowiednie. IDE nie czyni żadnych założeń dotyczących tych parametrów, nie będzie używać ich, a nie zezwoli użytkownikowi na modyfikację ich. Jeśli użytkownik chce zmienić ustawienia, środowisko IDE będzie wywoływać `SccGetProjPath` ponownie, przekazując w tej samej wartości odbierał poprzednio. Daje to wtyczka pełną kontrolę nad tych dwóch ciągów.  
  
 Aby uzyskać `lpUser`, IDE może przekazać nazwę użytkownika lub jego może po prostu przekazać wskaźnik do pustego ciągu. W przypadku nazwy użytkownika, wtyczka do kontroli źródła należy używać go jako domyślny. Jednak jeśli przekazano żadnej nazwy lub jeśli logowanie nie powiodło się o podanej nazwie, wtyczka powinien zostać wyświetlony monit użytkownika o nazwę logowania i przekaż nazwę z powrotem w `lpUser` po odebraniu prawidłową nazwą logowania. Ponieważ wtyczki mogą zmienić ten ciąg, IDE będzie zawsze Przydziel bufor o rozmiarze (`SCC_USER_LEN`+ 1).  
  
> [!NOTE]
>  Pierwszą akcją, który wykonuje IDE może być wywołania `SccOpenProject` funkcji lub `SccGetProjPath` funkcji. W związku z nich mają identyczne `lpUser` parametr, który umożliwia wtyczka do kontroli źródła do logowania użytkownika w dowolnym momencie. Nawet jeśli powrót z funkcji wskazuje błąd, wtyczkę należy podać ten ciąg z prawidłową nazwą logowania.  
  
 `lpLocalPath` jest to katalog, w którym użytkownik przechowuje projektu. Może być ciągiem pustym. Jeśli katalog nie jest obecnie zdefiniowany (jak w przypadku użytkowników, próby pobrania projektu z systemu kontroli źródła) i `bAllowChangePath` jest `TRUE`, wtyczka do kontroli źródła może monitować użytkownika o wprowadzenie danych lub użyj innej metody do umieszczenia jej ciąg do własnej `lpLocalPath`. Jeśli `bAllowChangePath` jest `FALSE`, wtyczka nie należy zmieniać ciągu, ponieważ użytkownik pracuje się już w określonym katalogu.  
  
 Jeśli użytkownik tworzy nowy projekt, które należy umieścić pod kontrolą źródła, wtyczka do kontroli źródła może nie tworzą go w systemie kontroli źródła w czasie `SccGetProjPath` jest wywoływana. Zamiast tego ponownie przekazuje ciąg wraz z wartość różną od zera dla `pbNew`, wskazujący, że projekt zostanie utworzony w systemie kontroli źródła.  
  
 Na przykład, jeśli użytkownik w **nowy projekt** kreatora w programie Visual Studio dodaje projekt lub jej do kontroli źródła, Visual Studio wywołuje tę funkcję i wtyczki Określa, czy można utworzyć nowy projekt w systemie kontroli źródła zawiera projekt programu Visual Studio. Jeśli użytkownik kliknie **anulować** przed zakończeniem działania kreatora, nigdy nie jest tworzony projekt. Jeśli użytkownik kliknie **OK**, Visual Studio wywołuje `SccOpenProject`, przekazując `SCC_OPT_CREATEIFNEW`, i projektu objętego kontrolą źródła jest tworzony w tym czasie.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)
