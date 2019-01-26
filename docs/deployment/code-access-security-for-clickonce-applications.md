---
title: Kod zabezpieczenia dostępu dla aplikacji ClickOnce | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ee9d478aa328337d3a2b08c74fcbbf7166580962
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55018348"
---
# <a name="code-access-security-for-clickonce-applications"></a>Zabezpieczenia dostępu kodu dla aplikacji ClickOnce
Aplikacje ClickOnce są oparte na programie .NET Framework i podlegają ograniczeniom zabezpieczeń dostępu kodu. Z tego powodu jest ważne, że rozumiesz implikacje kodu dostępu zabezpieczeń i w związku z tym zapisu aplikacji ClickOnce.  
  
 Zabezpieczenia dostępu kodu jest mechanizm programu .NET Framework, która ułatwia ograniczenie dostępu kodu do chronionych zasobów i operacji. Należy skonfigurować uprawnienia zabezpieczeń dostępu kodu dla aplikacji ClickOnce do używania strefy, które są odpowiednie dla lokalizacji Instalatora aplikacji. W większości przypadków można wybrać **Internet** strefę dla ograniczony zestaw uprawnień lub **lokalny Intranet** strefę dla większy zestaw uprawnień.  
  
## <a name="default-clickonce-code-access-security"></a>Domyślne zabezpieczenia dostępu kodu ClickOnce  
 Domyślnie aplikacji ClickOnce otrzymuje uprawnienia pełnego zaufania, po zainstalowaniu lub uruchomienia na komputerze klienckim.  
  
- Aplikacja mająca uprawnienia pełnego zaufania, ma nieograniczony dostęp do zasobów, takich jak system plików i rejestru. Dzięki temu potencjalnie aplikacji (i systemu przez użytkownika końcowego) została wykorzystana przez złośliwy kod.  
  
- Jeśli aplikacja wymaga uprawnień pełnego zaufania, użytkownik końcowy może być monitowani o nadanie uprawnień do aplikacji. Oznacza to, że aplikacja nie zapewnia naprawdę środowisko ClickOnce i monit może potencjalnie być mylące dla mniej doświadczonych użytkowników.  
  
  > [!NOTE]
  >  Podczas instalowania aplikacji z nośników wymiennych, takich jak dysk CD-ROM, użytkownik nie jest monitowany. Ponadto administrator sieci można skonfigurować zasad sieciowych tak, aby użytkownicy nie będą monitowani podczas instalacji aplikacji z zaufanego źródła. Aby uzyskać więcej informacji, zobacz [Przegląd wdrażania aplikacji zaufanego](../deployment/trusted-application-deployment-overview.md).  
  
  Aby ograniczyć uprawnienia dla aplikacji ClickOnce, można zmodyfikować uprawnienia zabezpieczeń dostępu kodu dla swojej aplikacji zażądać strefy, który najlepiej odpowiada wymaganiom uprawnienia wymagane przez aplikację. W większości przypadków można wybrać strefy, w którym aplikacja jest wdrażana. Na przykład, jeśli aplikacja jest aplikacja dla przedsiębiorstw, można użyć **lokalny Intranet** strefy. Jeśli aplikacja jest aplikacja internetowa, możesz użyć **Internet** strefy.  
  
## <a name="configure-security-permissions"></a>Konfigurowania uprawnień zabezpieczeń  
 Zawsze należy skonfigurować aplikacja ClickOnce, aby zażądać odpowiedniej strefy, aby ograniczyć uprawnienia zabezpieczeń dostępu kodu. Można skonfigurować uprawnienia zabezpieczeń na **zabezpieczeń** strony **projektanta projektu**.  
  
 **Zabezpieczeń** strony w **projektanta projektu** zawiera **włączenia ustawień zabezpieczeń technologii ClickOnce** pole wyboru. Gdy to pole wyboru jest zaznaczone, żądań dotyczących uprawnień zabezpieczeń są dodawane do manifestu wdrażania aplikacji. W trakcie instalacji użytkownik zostanie wyświetlony monit udzielić uprawnień, jeśli żądane uprawnienia przekroczyć domyślnych uprawnień dla strefy, w którym aplikacja jest wdrażana. Aby uzyskać więcej informacji, zobacz [jak: Włączenie ustawień zabezpieczeń technologii ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md).  
  
 Aplikacje wdrożone z różnych lokalizacji są przyznawane różne poziomy uprawnień bez monitowania użytkownika. Na przykład gdy aplikacja jest wdrażana z Internetu, odbiera bardzo restrykcyjny zestaw uprawnień. Podczas instalowania z lokalnego intranetu, odbierze więcej uprawnień i zainstalowany z dysku CD, otrzyma uprawnienia pełnego zaufania.  
  
 Jako punktu wyjścia do konfigurowania uprawnień, można wybrać strefy zabezpieczeń z **strefy** listy na **zabezpieczeń** strony. Jeśli aplikacja zostanie wdrożona potencjalnie z więcej niż jedną strefę, wybierz strefę za pomocą najniższych uprawnień. Aby uzyskać więcej informacji, zobacz [jak: Ustawienie strefy zabezpieczeń dla aplikacji ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md).  
  
 Właściwości, które można ustawić zależą od zestawu uprawnień; nie wszystkie zestawy uprawnień mają właściwości, można konfigurować. Aby uzyskać więcej informacji o pełnej listy uprawnień, którzy mogą zażądać aplikacji, zobacz <xref:System.Security.Permissions>. Aby uzyskać więcej informacji o tym, jak można ustawić uprawnień dla strefy niestandardowych, zobacz [jak: Ustawienie uprawnień niestandardowych dla aplikacji ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).  
  
## <a name="debug-an-application-that-has-restricted-permissions"></a>Debuguj aplikację, która ma ograniczone uprawnienia  
 Deweloperzy najprawdopodobniej uruchom komputer deweloperski przy użyciu uprawnień pełnego zaufania. W związku z tym nie ma tego samego wyjątki zabezpieczeń podczas debugowania aplikacji, które użytkownicy mogą zobaczyć, jeśli są uruchamiane z ograniczonymi uprawnieniami.  
  
 Aby przechwytywać te wyjątki, należy debugować aplikację za pomocą tych samych uprawnień jako użytkownik końcowy. Debugowanie przy użyciu ograniczonych uprawnień można włączyć dla **zabezpieczeń** strony **projektanta projektu**.  
  
 Podczas debugowania aplikacji przy użyciu ograniczonych uprawnień wyjątki zostanie wygenerowany dla żadnych wymogów bezpieczeństwa kodu, które nie zostały włączone na **zabezpieczeń** strony. Pomocnik wyjątków będą wyświetlane, podając sugestie dotyczące sposobu modyfikowania kodu, aby zapobiec wyjątku.  
  
 Ponadto podczas pisania kodu, funkcja IntelliSense w edytorze kodu spowoduje wyłączenie żadnych elementów członkowskich, które nie są uwzględnione w uprawnieniach zabezpieczeń, które zostały skonfigurowane.  
  
 Aby uzyskać więcej informacji, zobacz [jak: Debugowanie aplikacji ClickOnce z ograniczonymi uprawnieniami](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md).  
  
## <a name="security-permissions-for-browser-hosted-applications"></a>Uprawnienia zabezpieczeń dla aplikacji hostowanych w przeglądarce  
 Program Visual Studio zawiera następujące typy projektu aplikacji Windows Presentation Foundation (WPF):  
  
- Aplikacja Windows WPF  
  
- Aplikacja przeglądarki sieci Web środowiska WPF  
  
- Biblioteka kontrolek niestandardowych WPF  
  
- Biblioteka usługi WPF  
  
  Z tych typów projektów tylko WPF aplikacje przeglądarki sieci Web znajdują się w przeglądarce sieci Web i dlatego wymagają specjalnych wdrożenia i ustawienia zabezpieczeń. Domyślne ustawienia zabezpieczeń dla tych aplikacji są następujące:  
  
- **Włączenie ustawień zabezpieczeń technologii ClickOnce**  
  
- **Jest to aplikacja częściowej relacji zaufania**  
  
- **Strefy Internet** (z domyślnego zestawu uprawnień dla aplikacji przeglądarki sieci Web WPF wybrane)  
  
  W **Zaawansowane ustawienia zabezpieczeń** okno dialogowe **Debuguj aplikację z wybranym zestawem uprawnień** pole wyboru jest zaznaczony i wyłączony. Jest to spowodowane debugowanie w strefie nie może zostać wyłączone dla aplikacji hostowanych w przeglądarce.  
  
## <a name="see-also"></a>Zobacz także  
 [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Instrukcje: Włączenie ustawień zabezpieczeń technologii ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Instrukcje: Ustawienie strefy zabezpieczeń dla aplikacji ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Instrukcje: Ustawienie uprawnień niestandardowych dla aplikacji ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Instrukcje: Debugowanie aplikacji ClickOnce z ograniczonymi uprawnieniami](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Przegląd wdrażania zaufanych aplikacji](../deployment/trusted-application-deployment-overview.md)   
 [Strona zabezpieczeń, Projektant projektu](../ide/reference/security-page-project-designer.md)