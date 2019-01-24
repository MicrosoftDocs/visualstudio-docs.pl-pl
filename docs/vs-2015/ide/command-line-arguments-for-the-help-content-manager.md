---
title: Argumenty wiersza polecenia Menedżera zawartości pomocy | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-help-viewer
ms.topic: conceptual
ms.assetid: 3aa9890a-1147-42ba-adea-17935d184038
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ae1643b4a01c9bcab3878ec82b1808444cdc7712
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54778633"
---
# <a name="command-line-arguments-for-the-help-content-manager"></a>Argumenty wiersza poleceń Menedżera zawartości pomocy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można określić sposób wdrażania i zarządzania lokalną zawartością pomocy przy użyciu argumentów wiersza polecenia dla menedżera zawartości pomocy (HlpCtntmgr.exe). Należy uruchamiać skrypty dla tego narzędzia wiersza polecenia z uprawnieniami administratora, a te skrypty nie można uruchomić jako usługę. Za pomocą tego narzędzia, należy wykonać następujące zadania:  
  
- Dodaj lub Aktualizuj lokalną zawartość pomocy z dysku lub z chmury.  
  
- Usuń lokalną zawartość pomocy.  
  
- Przenieś magazynu zawartości lokalnej pomocy.  
  
- Dodawanie, aktualizowanie, usuń lub Przenieś lokalną zawartość pomocy dyskretnie.  
  
  Składnia:  
  
```  
HlpCtntmgr.exe /operation Value /catalogname CatalogName /locale Locale /sourceuri InstallationPoint  
```  
  
 Na przykład:  
  
```  
hlpctntmgr.exe /operation install /catalogname VisualStudio14 /locale en-us /sourceuri d:\productDocumentation\HelpContentSetup.msha  
```  
  
## <a name="switches-and-arguments"></a>Przełączniki i argumenty  
 W poniższej tabeli opisano przełączniki i argumenty, które służą do narzędzia wiersza polecenia dla menedżera zawartości pomocy:  
  
|Przełącznik|Wymagany?|Argumenty|  
|------------|---------------|---------------|  
|/Operation|Tak|-   **Zainstaluj**--dodaje książki ze źródła instalacji określonego do magazynu zawartości lokalnej.<br />     Ten przełącznik wymaga użycia argumentu/booklist i/lub argument/sourceuri. Jeśli nie zostanie określony argument/sourceuri, domyślne programu Visual Studio identyfikator URI jest używany jako źródło instalacji. Jeśli nie zostanie określony argument/booklist, zostaną zainstalowane wszystkie książki ze ścieżki/sourceuri.<br />-   **Odinstaluj**— usuwa książek, które określają z magazynu zawartości lokalnej.<br />     Ten przełącznik wymaga użycia argumentu/booklist lub/sourceuri.  Jeśli określono argument/sourceuri, zostaną usunięte wszystkie książki, a argument/booklist jest ignorowany.<br />-   **Przenieś**--przenosi Magazyn lokalny do ścieżki, który określisz. Domyślna ścieżka magazynu lokalnego jest ustawiana przez Instalatora pomocy w obszarze % PROGRAMDATA %<br />     Ten przełącznik wymaga argumentów/locationpath i/catalogname. Komunikaty o błędach będą rejestrowane w dzienniku zdarzeń, jeśli określona ścieżka nie jest prawidłowa, lub jeśli dysk zawiera za mało wolnego miejsca do przechowywania zawartości.<br />-   **Odśwież**--aktualizuje tematy, które zmieniły się od czasu gdy zostały zainstalowane lub ostatnio zaktualizowane.<br />     Ten przełącznik wymaga argumentu/sourceuri.|  
|/catalogName|Tak|Określa nazwę wykazu zawartości.|  
|/locale|Nie|Określa ustawienia regionalne produktu, który służy do wyświetlania i zarządzania zawartością w ramach bieżącego wystąpienia podglądu pomocy. Na przykład określić `EN-US` dla angielskiego stanów.<br /><br /> Jeśli nie określisz ustawień regionalnych, ustawienia regionalne systemu operacyjnego jest używany. Jeśli nie można ustalić ustawień regionalnych, `EN-US` jest używany.<br /><br /> Jeśli określisz ustawień regionalnych, które nie są prawidłowe, komunikat o błędzie jest rejestrowane w dzienniku zdarzeń.|  
|/e|Nie|Podnosi poziom uprawnień Menedżera zawartości pomocy do uprawnień administratora, jeśli bieżący użytkownik ma poświadczenia administracyjne.|  
|/sourceURI|Nie|Określa adres URL, z którego zawartość jest zainstalowany (interfejs API usługi) lub ścieżkę do pliku instalacyjnego zawartości (.msha). Adres URL może wskazywać grupę produktów (węzeł najwyższego poziomu) lub książki produktu (węzeł na poziomie liścia) w punkcie końcowym w stylu programu Visual Studio 2010. Nie trzeba dołączać kreski ukośnej (/) na końcu adresu URL. Jeśli dołączysz znaku ukośnika na końcu, będzie odpowiednio obsługiwany.<br /><br /> Komunikat o błędzie jest rejestrowany w przypadku dziennika, jeśli określisz plik, którego nie można odnaleźć, jest nieprawidłowy lub nie jest dostępny, lub, jeśli połączenie z Internetem nie jest dostępna lub zostanie przerwane, podczas gdy odbywa się zarządzanie zawartością.|  
|/vendor|Nie|Określa dostawcę zawartości produktu, która zostanie usunięta (na przykład `Microsoft`). Argument domyślny dla tego przełącznika to Microsoft.|  
|/productName|Nie|Określa nazwę produktu dla książek, które zostaną usunięte. Nazwa produktu jest zawarta w plikach helpcontentsetup.msha lub books.html, które są dostarczane z zawartości. Jednocześnie można usunąć księgi tylko z jednego produktu. Aby usunąć książki z wielu produktów, należy wykonać wiele instalacji.|  
|/ booklist|Nie|Określa nazwy książek, które mają być zarządzane, oddzielone spacjami. Wartości muszą odpowiadać nazwom książek, znajdującym znajdujących się na nośniku instalacyjnym.<br /><br /> Jeśli ten argument nie jest określony, wszystkie zalecane książki dla określonego produktu ścieżki/sourceuri są zainstalowane, jeśli źródło instalacji znajduje się w [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] formatu.<br /><br /> Jeśli nazwa książki zawiera jedną lub więcej spacji, Otocz ją podwójnymi cudzysłowami ("), tak aby lista była rozdzielana odpowiednio.<br /><br /> Jeśli określisz parametr/sourceuri, który jest nieprawidłowy lub nie jest osiągalny, będą rejestrowane komunikaty o błędach.|  
|/skuId|Nie|Określa jednostkę magazynową (SKU) produktu ze źródła instalacji i filtruje książki, które określa przełącznik/sourceuri.|  
|/Membership|Nie|-   **Minimalna**--instaluje minimalny zestaw zawartości pomocy, w oparciu o jednostki SKU, który określisz przy użyciu przełącznika/skuid. Mapowanie między jednostką SKU a zestawem zawartości jest uwidoczniony w interfejsie API usługi.<br />-   **Zaleca się**— instaluje zbiór zalecanych książek dla obiektu SKU, który określono za pomocą/argumentu skuid. Źródło instalacji jest interfejs API usługi lub. MSHA.<br />-   **Pełna**— instaluje cały zbiór książek dla obiektu SKU, który określono za pomocą/argumentu skuid. Źródło instalacji jest interfejs API usługi lub. MSHA.|  
|/ locationpath|Nie|Określa folder domyślny dla lokalnej zawartość pomocy. Należy użyć tego przełącznika, tylko do zainstalowania lub przenoszenia zawartości. Jeśli określisz tego przełącznika, należy także określić/silent przełącznika.|  
|/silent|Nie|Instaluje lub usuwa zawartość pomocy bez monitowania użytkownika ani wyświetlania żadnych interfejsów użytkownika, w tym ikony w obszarze powiadomień stanu. Wyjście jest rejestrowane w pliku w katalogu % Temp %. **Ważne:**  Do cichej instalacji zawartości, należy użyć plików .cab podpisanych cyfrowo, a nie plików .mshc.|  
|/launchingApp|Nie|Definiuje kontekst aplikacji i wykazu, w przypadku uruchomienia podglądu pomocy bez nadrzędnej aplikacji. Argumenty dla tego przełącznika to *CompanyName*, *ProductName*, i *Numerwersji* (na przykład `/launchingApp Microsoft,VisualStudio,11.0`).<br /><br /> Jest to wymagane do zainstalowania zawartości przy użyciu/silent parametru. "|  
|/ wait *sekund*|Nie|Wstrzymuje instalowanie, odinstalowywanie oraz operacji odświeżania. Jeśli operacja jest już w toku dla wykazu, proces będzie czekał do danej liczby sekund, aby kontynuować. Użycie wartości 0 spowoduje czekać w nieskończoność.|  
|/?|Nie|Wyświetla listę przełączników i ich opisów dla narzędzia wiersza polecenia dla menedżera zawartości pomocy.|  
  
### <a name="exit-codes"></a>Kody zakończenia  
 Po uruchomieniu narzędzia wiersza polecenia dla Help Content Managera w trybie dyskretnym, zwraca poniższe kody zakończenia:  
  
```  
Success = 0,  
  
FailureToElevate = 100  
InvalidCmdArgs = 101,  
FailOnFetchingOnlineContent = 110,  
FailOnFetchingContentFromDisk = 120,  
FailOnFetchingInstalledBooks = 130,  
NoBooksToUninstall = 200,  
NoBooksToInstall = 300,  
FailOnUninstall = 400,  
FailOnInstall = 500,  
FailOnMove = 600,  
FailOnUpdate = 700,  
FailOnRefresh = 800,  
Cancelled = 900,  
Others = 999,  
ContentManagementDisabled = 1200,  
OnlineHelpPreferenceDisabled = 1201  
UpdateAlreadyRunning = 1300 – (Signals that the update didn't run because another was in progress.)  
  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Podręcznik administratora programu Podgląd pomocy](../ide/help-viewer-administrator-guide.md)   
 [Przesłonięcia Menedżera zawartości Pomocy](../ide/help-content-manager-overrides.md)
