---
title: Zabezpieczenia dostępu kodu dla aplikacji ClickOnce | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- vb.XBAPProjectPropertiesSecurity.HowTo
- vb.XBAProjectPropertiesSecurity.HowTo
- vb.ProjectPropertiesSecurity.HowTo
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], security
- ClickOnce applications, caspol
- security [ClickOnce], WPF browser-hosted applications
- security [ClickOnce], ClickOnce applications
- ClickOnce applications, code access security policies
- security, ClickOnce
ms.assetid: 04b104d0-0bd3-4ccb-b164-1de92d234487
caps.latest.revision: 33
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 54160bbdfe834a1b3226f4445b862c151bcf35c3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64782943"
---
# <a name="code-access-security-for-clickonce-applications"></a>Zabezpieczenia dostępu kodu dla aplikacji ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aplikacje ClickOnce są oparte na .NET Framework i podlegają ograniczeniom zabezpieczeń dostępu kodu. Z tego powodu ważne jest, aby zrozumieć skutki zabezpieczenia dostępu kodu i odpowiednio napisać aplikacje ClickOnce.  
  
 Zabezpieczenia dostępu kodu to mechanizm w .NET Framework, który pomaga ograniczyć dostęp tego kodu do chronionych zasobów i operacji. Należy skonfigurować uprawnienia zabezpieczeń dostępu kodu dla aplikacji ClickOnce, aby używały strefy odpowiedniej dla lokalizacji Instalatora aplikacji. W większości przypadków można wybrać strefę **internetową** dla ograniczonego zestawu uprawnień lub strefy **Lokalny intranet** , aby uzyskać większy zestaw uprawnień.  
  
## <a name="default-clickonce-code-access-security"></a>Domyślne zabezpieczenia dostępu kodu ClickOnce  
 Domyślnie aplikacja ClickOnce otrzymuje uprawnienia pełnego zaufania, gdy jest zainstalowany lub uruchamiany na komputerze klienckim.  
  
- Aplikacja, która ma uprawnienia pełnego zaufania, ma nieograniczony dostęp do zasobów, takich jak system plików i rejestr. Dzięki temu aplikacja (i system użytkownika końcowego) mogą być wykorzystywane przez złośliwy kod.  
  
- Gdy aplikacja wymaga pełnych uprawnień zaufania, użytkownik końcowy może zostać poproszony o przyznanie uprawnień aplikacji. Oznacza to, że aplikacja nie zapewnia środowiska ClickOnce, a monit może być mylący dla mniej doświadczonych użytkowników.  
  
  > [!NOTE]
  > W przypadku instalowania aplikacji z nośników wymiennych, takich jak dysk CD-ROM, użytkownik nie jest monitowany. Ponadto administrator sieci może skonfigurować zasady sieciowe, aby użytkownicy nie monitowani o zainstalowanie aplikacji z zaufanego źródła. Aby uzyskać więcej informacji, zobacz [Omówienie wdrażania zaufanych aplikacji](../deployment/trusted-application-deployment-overview.md).  
  
  Aby ograniczyć uprawnienia aplikacji ClickOnce, można zmodyfikować uprawnienia zabezpieczeń dostępu kodu dla aplikacji w celu zażądania strefy, która najlepiej pasuje do uprawnień wymaganych przez aplikację. W większości przypadków można wybrać strefę, z której aplikacja jest wdrażana. Na przykład jeśli aplikacja jest aplikacją dla przedsiębiorstw, możesz użyć strefy **Lokalny intranet** . Jeśli aplikacja jest aplikacją internetową, możesz użyć strefy **Internet** .  
  
## <a name="configuring-security-permissions"></a>Konfigurowanie uprawnień zabezpieczeń  
 Należy zawsze skonfigurować aplikację ClickOnce, aby zażądać odpowiedniej strefy w celu ograniczenia uprawnień dostępu kodu. Uprawnienia zabezpieczeń można skonfigurować na stronie **zabezpieczenia** **projektanta projektu**.  
  
 Strona **zabezpieczenia** w **projektancie projektu** zawiera pole wyboru **Włącz ustawienia zabezpieczeń ClickOnce** . Gdy to pole wyboru jest zaznaczone, żądania uprawnień zabezpieczeń są dodawane do manifestu wdrożenia dla aplikacji. Podczas instalacji użytkownik zostanie poproszony o przyznanie uprawnień, jeśli żądane uprawnienia przekraczają domyślne uprawnienia dla strefy, z której aplikacja jest wdrażana. Aby uzyskać więcej informacji, zobacz [How to: Enable ClickOnce Security Settings](../deployment/how-to-enable-clickonce-security-settings.md).  
  
 Aplikacje wdrożone z różnych lokalizacji uzyskują różne poziomy uprawnień bez monitowania. Na przykład, gdy aplikacja jest wdrażana z Internetu, otrzymuje wysoce restrykcyjny zestaw uprawnień. Po zainstalowaniu z lokalnego intranetu otrzymuje więcej uprawnień i po zainstalowaniu z dysku CD-ROM otrzymuje uprawnienia pełnego zaufania.  
  
 Jako punkt początkowy konfigurowania uprawnień możesz wybrać strefę zabezpieczeń z listy **stref** na stronie **zabezpieczenia** . Jeśli aplikacja będzie potencjalnie wdrażana z więcej niż jednej strefy, wybierz strefę z najniższymi uprawnieniami. Aby uzyskać więcej informacji, zobacz [jak to zrobić: Ustawianie strefy zabezpieczeń dla aplikacji ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md).  
  
 Właściwości, które można ustawić, różnią się w zależności od zestawu uprawnień; nie wszystkie zestawy uprawnień mają konfigurowalne właściwości. Aby uzyskać więcej informacji na temat pełnej listy uprawnień, których aplikacja może żądać, zobacz <xref:System.Security.Permissions> . Aby uzyskać więcej informacji dotyczących sposobu ustawiania uprawnień dla strefy niestandardowej, zobacz [How to: Set Custom Permissions for a ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).  
  
## <a name="debugging-an-application-that-has-restricted-permissions"></a>Debugowanie aplikacji z ograniczonymi uprawnieniami  
 Jako deweloper, najprawdopodobniej uruchamiasz komputer deweloperski z pełnymi uprawnieniami zaufania. W związku z tym te same wyjątki zabezpieczeń nie są wyświetlane podczas debugowania aplikacji, które użytkownicy mogą zobaczyć po ich uruchomieniu z ograniczonymi uprawnieniami.  
  
 Aby przechwytywać te wyjątki, należy debugować aplikację z takimi samymi uprawnieniami jak użytkownik końcowy. Debugowanie z ograniczonymi uprawnieniami można włączyć na stronie **zabezpieczenia** **projektanta projektu**.  
  
 Podczas debugowania aplikacji z ograniczonymi uprawnieniami wyjątki zostaną zgłoszone w przypadku wszelkich wymagań dotyczących zabezpieczeń kodu, które nie zostały włączone na stronie **zabezpieczenia** . Zostanie wyświetlona pomocnik wyjątku z sugestiami dotyczącymi sposobu modyfikacji kodu w celu zapobieżenia wyjątku.  
  
 Ponadto podczas pisania kodu funkcja IntelliSense w edytorze kodu wyłącza wszystkie elementy członkowskie, które nie są uwzględnione w skonfigurowanych uprawnieniach zabezpieczeń.  
  
 Aby uzyskać więcej informacji, zobacz [How to: Debug The ClickOnce Application z ograniczonymi uprawnieniami](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md).  
  
## <a name="security-permissions-for-browser-hosted-applications"></a>Uprawnienia zabezpieczeń dla aplikacji hostowanych w przeglądarce  
 Program Visual Studio udostępnia następujące typy projektów dla aplikacji Windows Presentation Foundation (WPF):  
  
- Aplikacja WPF systemu Windows  
  
- Aplikacja przeglądarki sieci Web WPF  
  
- Biblioteka kontrolek niestandardowych WPF  
  
- Biblioteka usługi WPF  
  
  W przypadku tych typów projektu tylko aplikacje przeglądarki sieci Web WPF są hostowane w przeglądarce internetowej i dlatego wymagają specjalnego wdrożenia i ustawień zabezpieczeń. Domyślne ustawienia zabezpieczeń dla tych aplikacji są następujące:  
  
- **Włącz ustawienia zabezpieczeń ClickOnce**  
  
- **To jest częściowo zaufana aplikacja**  
  
- **Strefa internetowa** (z domyślnym zestawem uprawnień dla wybranych aplikacji przeglądarki sieci Web WPF)  
  
  W oknie dialogowym **Zaawansowane ustawienia zabezpieczeń** pole wyboru **Debuguj tę aplikację z wybranym zestawem uprawnień** jest zaznaczone i wyłączone. Dzieje się tak dlatego, że debugowanie w strefie nie może być wyłączone dla aplikacji hostowanych w przeglądarce.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Instrukcje: Włączanie ustawień zabezpieczeń technologii ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Instrukcje: Ustawianie strefy zabezpieczeń dla aplikacji ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Instrukcje: Ustawianie uprawnień niestandardowych dla aplikacji ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Instrukcje: debugowanie aplikacji ClickOnce z ograniczonymi uprawnieniami](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Omówienie wdrażania zaufanych aplikacji](../deployment/trusted-application-deployment-overview.md)   
 [Strona zabezpieczeń, Projektant projektu](../ide/reference/security-page-project-designer.md)
