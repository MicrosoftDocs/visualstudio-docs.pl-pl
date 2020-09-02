---
title: Uaktualnianie projektów | Microsoft Docs
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
ms.openlocfilehash: 8e838cb02aa1a620356f96d9e77f1752797ac409
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64787215"
---
# <a name="upgrading-projects"></a>Uaktualnianie projektów
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Zmiany w modelu projektu z jednej wersji programu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] na następną mogą wymagać uaktualnienia projektów i rozwiązań, aby mogły być uruchamiane w nowszej wersji. [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]Udostępnia interfejsy, które mogą służyć do implementowania obsługi uaktualniania we własnych projektach.  
  
## <a name="upgrade-strategies"></a>Strategie uaktualniania  
 W celu obsługi uaktualnienia wdrożenie systemu projektu musi definiować i implementować strategię uaktualniania. W celu określenia strategii możesz wybrać obsługę kopii zapasowych (SxS) obok siebie, kopii zapasowej lub obu tych funkcji.  
  
- Kopia zapasowa SxS oznacza, że projekt kopiuje tylko te pliki, które wymagają uaktualnienia w miejscu, dodając odpowiedni sufiks nazwy pliku, na przykład ". old".  
  
- Kopia zapasowa oznacza, że projekt kopiuje wszystkie elementy projektu do lokalizacji kopii zapasowej dostarczonej przez użytkownika. Odpowiednie pliki w oryginalnej lokalizacji projektu są następnie uaktualniane.  
  
## <a name="how-upgrade-works"></a>Jak działa uaktualnienie  
 Gdy rozwiązanie utworzone w starszej wersji programu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] jest otwarte w nowszej wersji, IDE sprawdza plik rozwiązania, aby ustalić, czy należy go uaktualnić. Jeśli jest wymagane uaktualnienie, **Kreator uaktualniania** zostanie automatycznie uruchomiony, aby przeprowadzić użytkownika przez proces uaktualniania.  
  
 Gdy rozwiązanie wymaga uaktualnienia, wysyła zapytanie do każdej fabryki projektu w celu jej strategii uaktualniania. Strategia określa, czy fabryka projektów obsługuje kopie zapasowe i kopie zapasowe SxS. Informacje są wysyłane do **Kreatora uaktualniania**, który zbiera informacje wymagane do utworzenia kopii zapasowej i przedstawia odpowiednie opcje dla użytkownika.  
  
### <a name="multi-project-solutions"></a>Rozwiązania obejmujące wiele projektów  
 Jeśli rozwiązanie zawiera wiele projektów, a strategie uaktualniania różnią się, na przykład gdy projekt C++ obsługuje tylko kopie zapasowe SxS i projekt sieci Web, który obsługuje tylko kopiowanie kopii zapasowych, fabryki projektu muszą negocjować strategię uaktualniania.  
  
 Rozwiązanie wysyła zapytanie do każdego fabryki projektu dla <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> . Następnie wywołuje, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> Aby zobaczyć, czy globalne pliki projektu wymagają uaktualnienia i określić obsługiwane strategie uaktualniania. Następnie zostanie wywołany **Kreator uaktualniania** .  
  
 Gdy użytkownik ukończy kreatora, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> jest wywoływana w każdej fabryce projektu, aby przeprowadzić rzeczywiste uaktualnienie. Aby ułatwić tworzenie kopii zapasowych, metody IVsProjectUpgradeViaFactory umożliwiają <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> usłudze rejestrowanie szczegółów procesu uaktualniania. Nie można buforować tej usługi.  
  
 Po zaktualizowaniu wszystkich odpowiednich plików globalnych każda fabryka projektu może wybrać utworzenie wystąpienia projektu. Implementacja projektu musi obsługiwać <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>Metoda jest następnie wywoływana w celu uaktualnienia wszystkich odpowiednich elementów projektu.  
  
> [!NOTE]
> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>Metoda nie zapewnia usługi SVsUpgradeLogger. Tę usługę można uzyskać, wywołując metodę <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> .  
  
## <a name="best-practices"></a>Najlepsze rozwiązania  
 Użyj <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> usługi, aby sprawdzić, czy możesz edytować plik przed jego edycją i zapisać go przed zapisaniem. Dzięki temu implementacje kopii zapasowych i uaktualnień będą obsługiwać pliki projektu pod kontrolą źródła, pliki z niewystarczającymi uprawnieniami i tak dalej.  
  
 Użyj <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> usługi podczas wszystkich faz tworzenia kopii zapasowych i uaktualniania, aby podać informacje o powodzeniu lub niepowodzeniu procesu uaktualniania.  
  
 Aby uzyskać więcej informacji na temat tworzenia kopii zapasowych i uaktualniania projektów, zobacz komentarze dotyczące IVsProjectUpgrade w vsshell2. idl.  
  
## <a name="see-also"></a>Zobacz też  
 [Projektami](../../extensibility/internals/projects.md)   
 [Uaktualnianie projektów niestandardowych](../../misc/upgrading-custom-projects.md)   
 [Uaktualnianie elementów projektu](../../misc/upgrading-project-items.md)
