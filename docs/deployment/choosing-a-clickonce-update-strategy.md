---
title: Wybieranie strategii aktualizacji ClickOnce | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- application updates, ClickOnce
- updates, ClickOnce
- ClickOnce deployment, update strategies
ms.assetid: d8b6e7bb-4ea0-47f3-91cd-48580bdceccc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: edba26d951afb0ba2215af4c0a0eac09b1c31513
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56608499"
---
# <a name="choose-a-clickonce-update-strategy"></a>Wybieranie strategii aktualizacji ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] może dostarczać automatyczne aktualizacje aplikacji. A [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji co jakiś czas odczytuje swój plik manifestu wdrożenia, aby zobaczyć, czy są dostępne aktualizacje do aplikacji. Jeśli są dostępne, jest pobierana i uruchamiana nowa wersja aplikacji. W celu zwiększenia wydajności pobierane są tylko pliki, które uległy zmianie.

 Podczas projektowania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji, należy ustalić strategię, jakiej aplikacja będzie używać do sprawdzania dostępności aktualizacji. Istnieją trzy podstawowe strategie, których można użyć: sprawdzanie, czy są dostępne aktualizacje podczas uruchamiania aplikacji, sprawdzanie, czy są dostępne aktualizacje po uruchomieniu aplikacji (za pomocą wątku działającego w tle) oraz utworzenie interfejsu użytkownika do obsługi aktualizacji.

 Ponadto można określić, jak często aplikacja będzie sprawdzać, czy są dostępne aplikacje, oraz że aktualizacje są wymagane.

> [!NOTE]
>  Aktualizacje aplikacji wymagają łączności sieciowej. W przypadku braku połączenia sieciowego aplikacja zostanie uruchomiona bez sprawdzania, czy są dostępne aktualizacje, niezależnie od wybranej strategii aktualizacji.

> [!NOTE]
>  W .NET Framework 2.0 i .NET Framework 3.0 dowolny czas Aplikacja sprawdza, czy aktualizacje, przed lub po uruchomieniu lub za pomocą \<xref:System.Deployment.Application > interfejsy API, należy ustawić `deploymentProvider` w manifeście wdrożenia. `deploymentProvider` Odnosi się element w programie Visual Studio do **zaktualizować lokalizację** na **aktualizacje** okna dialogowego **Publikuj** kartę. Ta reguła przestała obowiązywać w programie .NET Framework 3.5. Aby uzyskać więcej informacji, zobacz [wdrażania ClickOnce aplikacji do testowania i obsługi serwerów produkcyjnych bez Resigning](../deployment/deploying-clickonce-applications-for-testing-and-production-without-resigning.md).

## <a name="check-for-updates-after-application-startup"></a>Sprawdź dostępność aktualizacji po uruchomieniu aplikacji
 Gdy jest używana ta strategia, aplikacja będzie podejmować próby zlokalizowania i odczytania pliku manifestu wdrożenia w tle, podczas gdy inne jej funkcje będą normalnie działać. Jeśli będzie dostępna aktualizacja, po następnym uruchomieniu aplikacji użytkownik będzie monitowany o pobranie i zainstalowanie aktualizacji.

 Ta strategia sprawdza się najlepiej w przypadku połączeń sieciowych o niskiej przepustowości lub większych aplikacji, które mogą wymagać pobierania dużych plików.

 Aby włączyć tę strategię aktualizacji, kliknij przycisk **po uruchomieniu aplikacji** w **wybierz, kiedy aplikacja ma sprawdzać dostępność aktualizacji** części **aktualizacje aplikacji** okno dialogowe. Następnie określ interwał aktualizacji w sekcji **Określ, jak często aplikacja ma sprawdzać dostępność aktualizacji**.

 To jest taka sama, jak zmiana **aktualizacji** element we wdrożeniu manifestu w następujący sposób:

```xml
<!-- When to check for updates -->
<subscription>
   <update>
      <expiration maximumAge="6" unit="hours" />
   </update>
</subscription>
```

## <a name="check-for-updates-before-application-startup"></a>Sprawdź dostępność aktualizacji, przed uruchomieniem aplikacji
 Strategia domyślna polega na próbie zlokalizowania i przeczytania pliku manifestu wdrożenia przed uruchomieniem aplikacji. Gdy jest używana ta strategia, aplikacja będzie podejmować próby zlokalizowania i odczytania pliku manifestu wdrożenia za każdym razem, gdy użytkownik uruchomi aplikację. Jeśli będzie dostępna aktualizacja, zostanie ona pobrana i uruchomiona; w przeciwnym razie zostanie uruchomiona dotychczasowa wersja aplikacji.

 Ta strategia sprawdza się najlepiej w przypadku połączeń sieciowych o wysokiej przepustowości; opóźnienia w uruchamianiu aplikacji mogą być nieakceptowalnie długie w przypadku połączenia o niskiej przepustowości.

 Aby włączyć tę strategię aktualizacji, kliknij przycisk **przed uruchomieniem aplikacji** w **wybierz, kiedy aplikacja ma sprawdzać dostępność aktualizacji** części **aktualizacje aplikacji** okno dialogowe.

 To jest taka sama, jak zmiana **aktualizacji** element we wdrożeniu manifestu w następujący sposób:

```xml
<!-- When to check for updates -->
<subscription>
   <update>
      <beforeApplicationStartup />
   </update>
</subscription>
```

## <a name="make-updates-required"></a>Że aktualizacje są wymagane
 Możliwe są sytuacje, w których autor aplikacji będzie wymagał, aby użytkownicy używali zaktualizowanej wersji aplikacji. Na przykład może to być spowodowane wprowadzeniem zmian w zasobie zewnętrznym, takim jak usługa sieci Web, które uniemożliwią poprawne działanie wcześniejszych wersji aplikacji. W takim przypadku należy oznaczyć aktualizację jako wymaganą i uniemożliwić użytkownikom uruchamianie wcześniejszych wersji.

> [!NOTE]
>  Mimo że można wymagać aktualizacji, używając innych strategii aktualizacji, sprawdzanie **przed uruchomieniem aplikacji** jest jedynym sposobem zagwarantowania, że nie można uruchomić starszej wersji. Gdy podczas uruchamiania zostanie wykryta obowiązkowa aktualizacja, użytkownik będzie musiał zaakceptować aktualizację lub zamknąć aplikację.

 Aby oznaczyć aktualizację jako wymagane, kliknij przycisk **określanie minimalnej wymaganej wersji tej aplikacji** w **aplikacja aktualizuje** okna dialogowego pole, a następnie określ wersję publikacji (**główna**, **Pomocnicza**, **kompilacji**, **poprawki**), która określa najniższy numer wersji aplikacji, którą można zainstalować.

 To jest taka sama, jak ustawienie **minimumRequiredVersion** atrybutu **wdrożenia** elementu w pliku manifestu wdrożenia, na przykład:

```xml
<deployment install="true" minimumRequiredVersion="1.0.0.0">
```

## <a name="specify-update-intervals"></a>Określanie interwałów aktualizacji
 Można również określić, jak często aplikacja sprawdza dostępność aktualizacji. W tym celu należy określić, że aplikacja sprawdza dostępność aktualizacji po uruchomieniu, tak jak opisano w sekcji „Sprawdzanie, czy są dostępne aktualizacje, po uruchomieniu aplikacji” wcześniej w tym temacie.

 Aby określić interwał aktualizacji, ustaw **Określ, jak często aplikacja ma sprawdzać dostępność aktualizacji** właściwości w **aktualizacje aplikacji** okno dialogowe.

 To jest taka sama, jak ustawienie **maximumAge** i **jednostki** atrybuty **aktualizacji** elementu w manifeście wdrożenia.

 Na przykład można chcieć, aby sprawdzanie odbywało się przy każdym uruchomieniu aplikacji, raz w tygodniu lub raz w miesiącu. Jeśli w określonym czasie nie będzie dostępne połączenie z siecią, sprawdzanie dostępności aplikacji zostanie wykonane przy następnym uruchomieniu aplikacji.

## <a name="provide-a-user-interface-for-updates"></a>Udostępniają interfejs użytkownika aktualizacji
 Gdy jest używana ta strategia, deweloper aplikacji dostarcza interfejs użytkownika, który umożliwia użytkownikowi określenie, kiedy lub jak często aplikacja ma sprawdzać dostępność aktualizacji. Na przykład można dostarczyć polecenie „Sprawdź, czy są dostępne aktualizacje” albo okno dialogowe „Ustawienia aktualizacji”, w którym będzie można wybrać różne interwały aktualizacji. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Interfejsów API wdrożenia oferują strukturę umożliwiającą programowania z własnego interfejsu użytkownika aktualizacji. Aby uzyskać więcej informacji, zobacz <xref:System.Deployment.Application> przestrzeni nazw.

 Jeśli aplikacja używa interfejsów API wdrożenia do sterowania własną logiką obsługi aktualizacji, należy zablokować sprawdzanie dostępności aktualizacji, tak jak opisano w poniższej sekcji „Blokowanie sprawdzania dostępności aktualizacji”.

 Ta strategia sprawdza się najlepiej w sytuacji, gdy są potrzebne różne strategie aktualizacji dla różnych użytkowników.

## <a name="block-update-checking"></a>Blokowanie sprawdzania dostępności aktualizacji
 Można także spowodować, że aplikacja nigdy nie będzie sprawdzać dostępności aktualizacji. Na przykład, może mieć prostą aplikację, która nigdy nie zostaną zaktualizowane, ale chcesz korzystać z zalet łatwej instalacji zapewniają przez [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia.

 Warto też zablokować sprawdzanie dostępności, jeśli aplikacja używa interfejsów API wdrożenia do wykonywania własnych aktualizacji — aktualizacji zobacz "Udostępniają interfejs użytkownika aktualizacji" wcześniej w tym temacie.

 Aby zablokować sprawdzanie aktualizacji, wyczyść **aplikacja ma sprawdzać dostępność aktualizacji** pole wyboru w oknie dialogowym aktualizacje aplikacji.

 Możesz również zablokować sprawdzanie dostępności, usuwając aktualizacji `<Subscription>` tag z manifestu wdrożenia.

## <a name="permission-elevation-and-updates"></a>Podniesienie uprawnień i aktualizacje
 Jeśli nowa wersja [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacja wymaga wyższego poziomu zaufania, aby uruchomić niż poprzednia wersja [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] będzie monitował użytkownika, z prośbą o tym, jeśli chce aplikacji można udzielić tego wyższego poziomu zaufania. Jeśli użytkownik odmówi udzielenia wyższego poziomu zaufania, aktualizacja nie zostanie zainstalowana. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] będzie monitować użytkownika o ponowne zainstalowanie aplikacji, po ponownym uruchomieniu obok. Jeśli użytkownik odmówi w tym punkcie udzielenia wyższego poziomu zaufania, a aktualizacja nie będzie oznaczona jako wymagana, zostanie uruchomiona stara wersja aplikacji. Jeśli jednak aktualizacja będzie wymagana, aplikacja nie zostanie uruchomiona ponownie, dopóki użytkownik nie zaakceptuje wyższego poziomu zaufania.

 Użytkownicy nie będą monitowani o poziomy zaufania w przypadku użycia zaufanego wdrożenia aplikacji. Aby uzyskać więcej informacji, zobacz [Przegląd wdrażania aplikacji zaufanego](../deployment/trusted-application-deployment-overview.md).

## <a name="see-also"></a>Zobacz także
 \<xref:System.Deployment.Application>
- [Wdrażania i zabezpieczeń ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Wybieranie strategii wdrażania ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)
- [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)
- [Jak technologia ClickOnce wykonuje aktualizacje aplikacji](../deployment/how-clickonce-performs-application-updates.md)
- [Instrukcje: Zarządzanie aktualizacjami dla aplikacji ClickOnce](../deployment/how-to-manage-updates-for-a-clickonce-application.md)