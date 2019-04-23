---
title: Uaktualnianie projektów | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- upgrading VSPackages
- upgrading applications, strategies
- VSPackages, upgrade support
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7e97e21b2d08d7398a4372ac31cda63b5cfb9fe9
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60100602"
---
# <a name="upgrading-projects"></a>Uaktualnianie projektów
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Zmienia się na modelu projektu z jednej wersji [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] do następnego może wymagać projekty i rozwiązania uaktualnienia, aby umożliwić im uruchamianie w nowszej wersji. [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] Udostępnia interfejsy, które mogą służyć do implementowania obsługi uaktualnienia do własnych projektów.  
  
## <a name="upgrade-strategies"></a>Strategie uaktualniania  
 Do obsługi uaktualnienia, implementacji systemu projektu muszą definiować ani implementować strategię uaktualnienia. Przy określaniu strategii, istnieje możliwość obsługi kopii zapasowych side-by-side (SxS) i/lub kopii zapasowej.  
  
- Kopia zapasowa SxS oznacza to, czy projekt kopiuje tylko pliki wymagające uaktualnienia w miejscu, dodając sufiks nazwy odpowiedni plik, na przykład ".old".  
  
- Kopii zapasowej oznacza to, czy projekt kopiuje wszystkie elementy projektu do podanego przez użytkownika lokalizacji kopii zapasowej. Następnie uaktualniane są odpowiednie pliki w oryginalnej lokalizacji projektu.  
  
## <a name="how-upgrade-works"></a>Jak uaktualnić działa  
 Gdy rozwiązanie utworzone w starszych wersjach [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] jest otwarty w nowszej wersji kontroli środowiska IDE, w pliku rozwiązania, aby określić, jeśli musi zostać uaktualniony. Jeśli uaktualnianie jest wymagane, **Kreatora uaktualniania** jest uruchamiane automatycznie przeprowadzi użytkownika przez proces uaktualniania.  
  
 To rozwiązanie wymaga uaktualnienia, wysyła zapytanie każda fabryka projektu dla jego strategii uaktualniania. Strategii, która określa, czy fabryka projektu obsługuje kopii zapasowej lub kopii zapasowej SxS. Informacje są wysyłane do **Kreatora uaktualniania**, która zbiera informacje wymagane do tworzenia kopii zapasowej i wyświetlane odpowiednie opcje dla użytkownika.  
  
### <a name="multi-project-solutions"></a>Rozwiązania dotyczące wielu projektów  
 Jeśli rozwiązanie zawiera wiele projektów i uaktualniania strategie są różne, np. gdy projekt C++, który obsługuje tylko SxS kopii zapasowej, a projekt sieci Web, które obsługują tylko kopii zapasowej, fabryk projektów muszą uzgodnić strategii uaktualniania.  
  
 Rozwiązanie zapytania każda fabryka projektu dla <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>. Następnie wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> Zobacz, czy pliki projektu globalnego wymagają, uaktualnianie i określenia obsługiwanych strategie uaktualnienia. **Kreatora uaktualniania** zostanie następnie wywołana.  
  
 Po użytkownik Dokańcza pracę z kreatorem, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> jest wywoływana w każdej fabryki projektu do wykonania rzeczywistego uaktualnienia. W celu ułatwienia kopii zapasowej, zapewniają metody IVsProjectUpgradeViaFactory <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> usługę, aby rejestrować szczegóły procesu uaktualniania. Nie można buforować tej usługi.  
  
 Po zaktualizowaniu wszystkie odpowiednie pliki globalnego, każda fabryka projektu można utworzyć projektu. Implementacja projektu musi obsługiwać <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> Wywoływana jest metoda następnie uaktualnić wszystkie elementy projektu.  
  
> [!NOTE]
>  <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> Metody nie dostarcza usługi SVsUpgradeLogger. Tę usługę można uzyskać przez wywołanie metody <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>.  
  
## <a name="best-practices"></a>Najlepsze praktyki  
 Użyj <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> usługi Sprawdź, czy można edytować plik przed jego edycji i można go zapisać przed zapisaniem zmian. Ułatwi to kopia zapasowa i uaktualniania implementacje obsługują pliki projektu objętego kontrolą źródła, pliki o niewystarczających uprawnieniach i tak dalej.  
  
 Użyj <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> usługi podczas wszystkich etapów tworzenia kopii zapasowej i uaktualniania zawiera informacje na temat powodzenie lub niepowodzenie procesu uaktualniania.  
  
 Aby uzyskać więcej informacji na temat tworzenia kopii zapasowych i uaktualnianie projektów znajdują się komentarze IVsProjectUpgrade w vsshell2.idl.  
  
## <a name="see-also"></a>Zobacz też  
 [Projekty](../../extensibility/internals/projects.md)   
 [Uaktualnianie projektów niestandardowych](../../misc/upgrading-custom-projects.md)   
 [Uaktualnianie elementów projektu](../../misc/upgrading-project-items.md)
