---
title: Wybieranie strategii aktualizacji ClickOnce | Microsoft Docs
description: Dowiedz się, w jaki sposób aplikacja ClickOnce obsługuje aktualizacje automatyczne i które strategie aktualizacji, których można użyć.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 5618a8996b9858f0799f2a359573d5b7b9da1ce9
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2020
ms.locfileid: "94383160"
---
# <a name="choose-a-clickonce-update-strategy"></a>Wybieranie strategii aktualizacji ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] może zapewnić automatyczne aktualizacje aplikacji. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Aplikacja okresowo odczytuje plik manifestu wdrożenia, aby sprawdzić, czy są dostępne aktualizacje aplikacji. Jeśli są dostępne, jest pobierana i uruchamiana nowa wersja aplikacji. W celu zwiększenia wydajności pobierane są tylko pliki, które uległy zmianie.

 Podczas projektowania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji należy określić strategię używaną przez aplikację do sprawdzania dostępności aktualizacji. Istnieją trzy podstawowe strategie, których można użyć: sprawdzanie, czy są dostępne aktualizacje podczas uruchamiania aplikacji, sprawdzanie, czy są dostępne aktualizacje po uruchomieniu aplikacji (za pomocą wątku działającego w tle) oraz utworzenie interfejsu użytkownika do obsługi aktualizacji.

 Ponadto można określić, jak często aplikacja będzie sprawdzać, czy są dostępne aplikacje, oraz że aktualizacje są wymagane.

> [!NOTE]
> Aktualizacje aplikacji wymagają łączności sieciowej. W przypadku braku połączenia sieciowego aplikacja zostanie uruchomiona bez sprawdzania, czy są dostępne aktualizacje, niezależnie od wybranej strategii aktualizacji.

> [!NOTE]
> W .NET Framework 2,0 i .NET Framework 3,0, gdy aplikacja sprawdzi aktualizacje, przed rozpoczęciem lub po uruchomieniu lub przy użyciu \<xref:System.Deployment.Application> interfejsów API, należy ustawić `deploymentProvider` w manifeście wdrożenia. `deploymentProvider`Element odpowiada w programie Visual Studio w polu **Lokalizacja aktualizacji** w oknie dialogowym **aktualizacje** na karcie **Publikowanie** . Ta reguła jest swobodna w .NET Framework 3,5. Aby uzyskać więcej informacji, zobacz [wdrażanie aplikacji ClickOnce do testowania i serwerów produkcyjnych bez konieczności ich rejestracji](../deployment/deploying-clickonce-applications-for-testing-and-production-without-resigning.md).

## <a name="check-for-updates-after-application-startup"></a>Sprawdź dostępność aktualizacji po uruchomieniu aplikacji
 Gdy jest używana ta strategia, aplikacja będzie podejmować próby zlokalizowania i odczytania pliku manifestu wdrożenia w tle, podczas gdy inne jej funkcje będą normalnie działać. Jeśli będzie dostępna aktualizacja, po następnym uruchomieniu aplikacji użytkownik będzie monitowany o pobranie i zainstalowanie aktualizacji.

 Ta strategia sprawdza się najlepiej w przypadku połączeń sieciowych o niskiej przepustowości lub większych aplikacji, które mogą wymagać pobierania dużych plików.

 Aby włączyć tę strategię aktualizacji, kliknij pozycję **po uruchomieniu aplikacji** w sekcji **Wybierz, kiedy aplikacja powinna sprawdzać dostępność aktualizacji** w oknie dialogowym **aktualizacje aplikacji** . Następnie określ interwał aktualizacji w sekcji **Określ, jak często aplikacja ma sprawdzać dostępność aktualizacji**.

 Jest to takie samo jak zmiana elementu **Update** w manifeście wdrożenia w następujący sposób:

```xml
<!-- When to check for updates -->
<subscription>
   <update>
      <expiration maximumAge="6" unit="hours" />
   </update>
</subscription>
```

## <a name="check-for-updates-before-application-startup"></a>Wyszukaj aktualizacje przed uruchomieniem aplikacji
 Strategia domyślna polega na próbie zlokalizowania i przeczytania pliku manifestu wdrożenia przed uruchomieniem aplikacji. Gdy jest używana ta strategia, aplikacja będzie podejmować próby zlokalizowania i odczytania pliku manifestu wdrożenia za każdym razem, gdy użytkownik uruchomi aplikację. Jeśli będzie dostępna aktualizacja, zostanie ona pobrana i uruchomiona; w przeciwnym razie zostanie uruchomiona dotychczasowa wersja aplikacji.

 Ta strategia sprawdza się najlepiej w przypadku połączeń sieciowych o wysokiej przepustowości; opóźnienia w uruchamianiu aplikacji mogą być nieakceptowalnie długie w przypadku połączenia o niskiej przepustowości.

 Aby włączyć tę strategię aktualizacji, kliknij przycisk **przed uruchomieniem aplikacji** w sekcji **Wybierz, kiedy aplikacja powinna sprawdzać dostępność aktualizacji** w oknie dialogowym **aktualizacje aplikacji** .

 Jest to takie samo jak zmiana elementu **Update** w manifeście wdrożenia w następujący sposób:

```xml
<!-- When to check for updates -->
<subscription>
   <update>
      <beforeApplicationStartup />
   </update>
</subscription>
```

## <a name="make-updates-required"></a>Wymagane aktualizacje
 Możliwe są sytuacje, w których autor aplikacji będzie wymagał, aby użytkownicy używali zaktualizowanej wersji aplikacji. Na przykład może to być spowodowane wprowadzeniem zmian w zasobie zewnętrznym, takim jak usługa sieci Web, które uniemożliwią poprawne działanie wcześniejszych wersji aplikacji. W takim przypadku należy oznaczyć aktualizację jako wymaganą i uniemożliwić użytkownikom uruchamianie wcześniejszych wersji.

> [!NOTE]
> Mimo że można wymagać aktualizacji przy użyciu innych strategii aktualizacji, sprawdzenie **przed uruchomieniem aplikacji** jest jedynym sposobem na zagwarantowanie, że nie można uruchomić starszej wersji. Gdy podczas uruchamiania zostanie wykryta obowiązkowa aktualizacja, użytkownik będzie musiał zaakceptować aktualizację lub zamknąć aplikację.

 Aby oznaczyć aktualizację jako wymaganą, kliknij pozycję **Określ minimalną wersję wymaganą dla tej aplikacji** w oknie dialogowym **aktualizacje aplikacji** , a następnie określ wersję publikacji ( **główna** , **pomocnicza** , **kompilacja** , **poprawka** ), która określa najniższy numer wersji aplikacji, która może być zainstalowana.

 Jest to takie samo, jak ustawienie atrybutu **MinimumRequiredVersion** elementu **Deployment** w manifeście wdrożenia; na przykład:

```xml
<deployment install="true" minimumRequiredVersion="1.0.0.0">
```

## <a name="specify-update-intervals"></a>Określanie interwałów aktualizacji
 Można również określić, jak często aplikacja sprawdza dostępność aktualizacji. W tym celu należy określić, że aplikacja sprawdza dostępność aktualizacji po uruchomieniu, tak jak opisano w sekcji „Sprawdzanie, czy są dostępne aktualizacje, po uruchomieniu aplikacji” wcześniej w tym temacie.

 Aby określić interwał aktualizacji, ustaw właściwości **Określ, jak często aplikacja ma sprawdzać dostępność aktualizacji** w oknie dialogowym **aktualizacje aplikacji** .

 Jest to takie samo, jak ustawienie wartości **Maksymalna** i atrybuty **jednostki** elementu **Update** w manifeście wdrożenia.

 Na przykład można chcieć, aby sprawdzanie odbywało się przy każdym uruchomieniu aplikacji, raz w tygodniu lub raz w miesiącu. Jeśli w określonym czasie nie będzie dostępne połączenie z siecią, sprawdzanie dostępności aplikacji zostanie wykonane przy następnym uruchomieniu aplikacji.

## <a name="provide-a-user-interface-for-updates"></a>Podaj interfejs użytkownika dla aktualizacji
 Gdy jest używana ta strategia, deweloper aplikacji dostarcza interfejs użytkownika, który umożliwia użytkownikowi określenie, kiedy lub jak często aplikacja ma sprawdzać dostępność aktualizacji. Na przykład można dostarczyć polecenie „Sprawdź, czy są dostępne aktualizacje” albo okno dialogowe „Ustawienia aktualizacji”, w którym będzie można wybrać różne interwały aktualizacji. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Interfejsy API wdrażania zapewniają platformę do programowania własnego interfejsu użytkownika aktualizacji. Aby uzyskać więcej informacji, zobacz <xref:System.Deployment.Application> przestrzeń nazw.

 Jeśli aplikacja używa interfejsów API wdrożenia do sterowania własną logiką obsługi aktualizacji, należy zablokować sprawdzanie dostępności aktualizacji, tak jak opisano w poniższej sekcji „Blokowanie sprawdzania dostępności aktualizacji”.

 Ta strategia sprawdza się najlepiej w sytuacji, gdy są potrzebne różne strategie aktualizacji dla różnych użytkowników.

## <a name="block-update-checking"></a>Blokuj sprawdzanie aktualizacji
 Można także spowodować, że aplikacja nigdy nie będzie sprawdzać dostępności aktualizacji. Można na przykład utworzyć prostą aplikację, która nigdy nie będzie aktualizowana, ale chcesz wykorzystać łatwość instalacji zapewnianą przez [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenie.

 Należy również zablokować sprawdzanie aktualizacji, jeśli aplikacja używa interfejsów API wdrażania do wykonywania własnych aktualizacji; Zobacz sekcję "Dostarczanie interfejsu użytkownika do aktualizacji" wcześniej w tym temacie.

 Aby zablokować sprawdzanie aktualizacji, wyczyść pole wyboru **aplikacja powinna sprawdzać dostępność aktualizacji** w oknie dialogowym aktualizacje aplikacji.

 Sprawdzanie aktualizacji można także zablokować przez usunięcie `<Subscription>` znacznika z manifestu wdrożenia.

## <a name="permission-elevation-and-updates"></a>Podniesienie uprawnień i aktualizacje
 Jeśli nowa wersja [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji wymaga, aby był uruchamiany wyższy poziom zaufania niż poprzednia wersja, program wyświetli [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] monit z pytaniem, czy chcemy, aby aplikacja udzieliła wyższego poziomu zaufania. Jeśli użytkownik odmówi udzielenia wyższego poziomu zaufania, aktualizacja nie zostanie zainstalowana. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] monituje użytkownika o ponowne zainstalowanie aplikacji po ponownym uruchomieniu. Jeśli użytkownik odmówi w tym punkcie udzielenia wyższego poziomu zaufania, a aktualizacja nie będzie oznaczona jako wymagana, zostanie uruchomiona stara wersja aplikacji. Jeśli jednak aktualizacja będzie wymagana, aplikacja nie zostanie uruchomiona ponownie, dopóki użytkownik nie zaakceptuje wyższego poziomu zaufania.

 Użytkownicy nie będą monitowani o poziomy zaufania w przypadku użycia zaufanego wdrożenia aplikacji. Aby uzyskać więcej informacji, zobacz [Omówienie wdrażania zaufanych aplikacji](../deployment/trusted-application-deployment-overview.md).

## <a name="see-also"></a>Zobacz też
 \<xref:System.Deployment.Application>
- [Zabezpieczenia i wdrażanie technologii ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Wybieranie strategii wdrażania technologii ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)
- [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)
- [Jak technologia ClickOnce wykonuje aktualizacje aplikacji](../deployment/how-clickonce-performs-application-updates.md)
- [Instrukcje: Zarządzanie aktualizacjami aplikacji ClickOnce](../deployment/how-to-manage-updates-for-a-clickonce-application.md)
