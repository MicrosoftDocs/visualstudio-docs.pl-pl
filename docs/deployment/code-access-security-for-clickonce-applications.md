---
title: Zabezpieczenia dostępu do kodu dla aplikacji ClickOnce | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 9fd2d9b6792cae002967c9000474a825bd3a0651
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649278"
---
# <a name="code-access-security-for-clickonce-applications"></a>Zabezpieczenia dostępu kodu dla aplikacji ClickOnce
ClickOnce aplikacje są oparte na .NET Framework i podlegają ograniczeniom zabezpieczeń dostępu do kodu. Z tego powodu ważne jest, aby zrozumieć implikacje zabezpieczeń dostępu do kodu i napisać aplikacje ClickOnce odpowiednio.

 Zabezpieczenia dostępu do kodu to mechanizm w programie .NET Framework, który pomaga ograniczyć dostęp, który kod ma do chronionych zasobów i operacji. Należy skonfigurować uprawnienia zabezpieczeń dostępu do kodu dla aplikacji ClickOnce, aby używać strefy odpowiedniej dla lokalizacji instalatora aplikacji. W większości przypadków można wybrać strefę **Internet** dla ograniczonego zestawu uprawnień lub strefę **Lokalny intranet** dla większego zestawu uprawnień.

## <a name="default-clickonce-code-access-security"></a>Domyślne zabezpieczenia dostępu do kodu ClickOnce
 Domyślnie aplikacja ClickOnce otrzymuje uprawnienia pełnego zaufania, gdy jest zainstalowana lub uruchamiana na komputerze klienckim.

- Aplikacja, która ma uprawnienia Pełnego zaufania ma nieograniczony dostęp do zasobów, takich jak system plików i rejestr. Potencjalnie umożliwia to wykorzystanie aplikacji (i systemu użytkownika końcowego) przez złośliwy kod.

- Gdy aplikacja wymaga uprawnień pełnego zaufania, użytkownik końcowy może zostać poproszony o przyznanie uprawnień do aplikacji. Oznacza to, że aplikacja nie naprawdę zapewniają clickonce doświadczenie, a monit może potencjalnie być mylące dla mniej doświadczonych użytkowników.

  > [!NOTE]
  > Podczas instalowania aplikacji z nośników wymiennych, takich jak dysk CD-ROM, użytkownik nie jest monitowany. Ponadto administrator sieci może skonfigurować zasady sieciowe, aby użytkownicy nie byli monitowani podczas instalowania aplikacji z zaufanego źródła. Aby uzyskać więcej informacji, zobacz [Omówienie wdrażania zaufanych aplikacji](../deployment/trusted-application-deployment-overview.md).

  Aby ograniczyć uprawnienia dla clickonce aplikacji, można zmodyfikować uprawnienia zabezpieczeń dostępu do kodu dla aplikacji, aby zażądać strefy, która najlepiej pasuje do uprawnień, które wymaga aplikacji. W większości przypadków można wybrać strefę, z której jest wdrażana aplikacja. Na przykład jeśli aplikacja jest aplikacją przedsiębiorstwa, można użyć lokalnej strefy **intranetu.** Jeśli aplikacja jest aplikacją internetową, można użyć strefy **Internet.**

## <a name="configure-security-permissions"></a>Konfigurowanie uprawnień zabezpieczeń
 Zawsze należy skonfigurować aplikację ClickOnce, aby zażądać odpowiedniej strefy, aby ograniczyć uprawnienia zabezpieczeń dostępu do kodu. Uprawnienia zabezpieczeń można skonfigurować na stronie **Zabezpieczenia** **projektanta projektu**.

 Strona **Zabezpieczenia** w **projektancie projektu** zawiera pole wyboru Włącz **kliknięciezadanie zabezpieczeń.** Gdy to pole wyboru jest zaznaczone, żądania uprawnień zabezpieczeń są dodawane do manifestu wdrażania dla aplikacji. W czasie instalacji użytkownik zostanie poproszony o przyznanie uprawnień, jeśli żądane uprawnienia przekraczają domyślne uprawnienia do strefy, z której jest wdrażana aplikacja. Aby uzyskać więcej informacji, zobacz [Jak: Włączanie ustawień zabezpieczeń ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md).

 Aplikacje wdrożone z różnych lokalizacji są przyznawane różne poziomy uprawnień bez monitowania. Na przykład gdy aplikacja jest wdrażana z Internetu, otrzymuje bardzo restrykcyjny zestaw uprawnień. Po zainstalowaniu z lokalnego intranetu otrzymuje więcej uprawnień, a po zainstalowaniu z dysku CD-ROM otrzymuje uprawnienia pełnego zaufania.

 Jako punkt wyjścia do konfigurowania uprawnień można wybrać strefę zabezpieczeń z listy **Strefa** na stronie **Zabezpieczenia.** Jeśli aplikacja zostanie potencjalnie wdrożona z więcej niż jednej strefy, wybierz strefę z najmniejszymi uprawnieniami. Aby uzyskać więcej informacji, zobacz [Jak: Ustawianie strefy zabezpieczeń dla aplikacji ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md).

 Właściwości, które można ustawić różnią się w zależności od zestawu uprawnień; nie wszystkie zestawy uprawnień mają konfigurowalne właściwości. Aby uzyskać więcej informacji na temat pełnej listy <xref:System.Security.Permissions>uprawnień, o które może zażądać aplikacja, zobacz . Aby uzyskać więcej informacji na temat ustawiania uprawnień do strefy niestandardowej, zobacz [Jak: Ustawianie niestandardowych uprawnień dla aplikacji ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).

## <a name="debug-an-application-that-has-restricted-permissions"></a>Debugowanie aplikacji z ograniczonymi uprawnieniami
 Jako deweloper najprawdopodobniej uruchamiasz komputer deweloperski z uprawnieniami Pełnego zaufania. W związku z tym nie są widoczne te same wyjątki zabezpieczeń podczas debugowania aplikacji, które użytkownicy mogą zobaczyć po uruchomieniu go z ograniczonymi uprawnieniami.

 Aby wychwytywać te wyjątki, należy debugować aplikację z tymi samymi uprawnieniami co użytkownik końcowy. Debugowanie z ograniczonymi uprawnieniami można włączyć na stronie **Zabezpieczenia** **projektanta projektu**.

 Podczas debugowania aplikacji z ograniczonymi uprawnieniami wyjątki będą zgłaszane dla wszelkich żądań zabezpieczeń kodu, które nie zostały włączone na stronie **Zabezpieczenia.** Pojawi się pomocnik wyjątku, podając sugestie dotyczące modyfikowania kodu, aby zapobiec wyjątek.

 Ponadto podczas pisania kodu funkcja IntelliSense w Edytorze kodu wyłączy wszystkie elementy członkowskie, które nie są uwzględnione w skonfigurowanych uprawnieniach zabezpieczeń.

 Aby uzyskać więcej informacji, zobacz [Jak: Debugowanie aplikacji ClickOnce z ograniczonymi uprawnieniami](securing-clickonce-applications.md).

## <a name="security-permissions-for-browser-hosted-applications"></a>Uprawnienia zabezpieczeń dla aplikacji hostowanych w przeglądarce
 Program Visual Studio udostępnia następujące typy projektów dla aplikacji Windows Presentation Foundation (WPF):

- Aplikacja WPF dla systemu Windows

- Aplikacja przeglądarki sieci Web WPF

- Biblioteka kontrolek niestandardowych WPF

- Biblioteka usług WPF

  Z tych typów projektu tylko aplikacje przeglądarki sieci Web WPF są hostowane w przeglądarce sieci Web i dlatego wymagają specjalnych ustawień wdrażania i zabezpieczeń. Domyślne ustawienia zabezpieczeń dla tych aplikacji są następujące:

- **Włącz ustawienia zabezpieczeń ClickOnce**

- **Jest to aplikacja częściowego zaufania**

- **Strefa internetowa** (z domyślnym ustawieniem uprawnień dla wybranych aplikacji przeglądarki sieci Web WPF)

  W oknie dialogowym **Zaawansowane ustawienia zabezpieczeń** pole wyboru **Debugowanie tej aplikacji z wybranym zestawem uprawnień** jest zaznaczone i wyłączone. Jest tak, ponieważ debugowania w strefie nie można wyłączyć dla aplikacji hostowanych przez przeglądarkę.

## <a name="see-also"></a>Zobacz też
- [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)
- [Jak: Włącz ustawienia zabezpieczeń ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)
- [Jak: Ustawianie strefy zabezpieczeń dla aplikacji ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [Jak: Ustawianie uprawnień niestandardowych dla aplikacji ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Jak: Debugowanie aplikacji ClickOnce z ograniczonymi uprawnieniami](securing-clickonce-applications.md)
- [Omówienie wdrażania zaufanych aplikacji](../deployment/trusted-application-deployment-overview.md)
- [Strona zabezpieczeń, Projektant projektu](../ide/reference/security-page-project-designer.md)