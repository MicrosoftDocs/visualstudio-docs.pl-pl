---
title: Lokalizowanie aplikacji ClickOnce | Microsoft Docs
description: Dowiedz się więcej na temat trzech sposobów lokalizowania aplikacji ClickOnce do wersji odpowiedniej dla określonej kultury.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- WPF, ClickOnce applications
- ClickOnce deployment, globalization
- deploying applications [ClickOnce], localizing ClickOnce applications
- localization, ClickOnce deployment
- ClickOnce deployment, download on-demand
- ClickOnce deployment, localization
- Windows Forms, ClickOnce applications
- console applications, ClickOnce applications
ms.assetid: c92b193b-054d-4923-834b-d4226a4c7a1a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 97c4fe8d72cc8e2216ee8f5057d032c071974bf3
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2020
ms.locfileid: "94350832"
---
# <a name="localize-clickonce-applications"></a>Lokalizowanie aplikacji ClickOnce
Lokalizacja to proces tworzenia aplikacji odpowiedniej dla określonej kultury. Ten proces obejmuje przetłumaczenie tekstu interfejsu użytkownika do języka właściwego dla regionu, przy użyciu poprawnego formatowania daty i waluty, dostosowania rozmiaru kontrolek w formularzu i kontroli dublowania od prawej do lewej w razie potrzeby.

 Lokalizowanie aplikacji spowoduje utworzenie jednego lub większej liczby zestawów satelickich. Każdy zestaw zawiera ciągi interfejsu użytkownika, obrazy i inne zasoby charakterystyczne dla danej kultury. (Główny plik wykonywalny aplikacji zawiera ciągi dla domyślnej kultury aplikacji).

 W tym temacie opisano trzy sposoby wdrażania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji dla innych kultur:

- Uwzględnij wszystkie zestawy satelickie w jednym wdrożeniu.

- Generuj jedno wdrożenie dla każdej kultury, z jednym zestawem satelickim dołączonym do każdego z nich.

- Pobierz zestawy satelickie na żądanie.

## <a name="including-all-satellite-assemblies-in-a-deployment"></a>Uwzględnianie wszystkich zestawów satelickich we wdrożeniu
 Zamiast publikować wiele [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożeń, można opublikować jedno [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenie zawierające wszystkie zestawy satelickie.

 Ta metoda jest wartością domyślną w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Aby użyć tej metody w programie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , nie trzeba wykonywać żadnych dodatkowych czynności.

 Aby użyć tej metody z *MageUI.exe* , należy ustawić kulturę dla aplikacji na **neutralną** w *MageUI.exe*. Następnie musisz ręcznie uwzględnić wszystkie zestawy satelickie we wdrożeniu. W *MageUI.exe* można dodać zestawy satelickie przy użyciu przycisku **Wypełnij** na karcie **pliki** manifestu aplikacji.

 Zaletą tego podejścia jest utworzenie jednego wdrożenia i uproszczenie zlokalizowanego scenariusza wdrożenia. W czasie wykonywania odpowiedni zestaw satelicki zostanie użyty w zależności od domyślnej kultury systemu operacyjnego Windows użytkownika. Wadą tego podejścia jest to, że pobieranie wszystkich zestawów satelickich za każdym razem, gdy aplikacja zostanie zainstalowana lub zaktualizowana na komputerze klienckim. Jeśli aplikacja ma dużą liczbę ciągów lub klienci mają wolne połączenie sieciowe, ten proces może mieć wpływ na wydajność podczas aktualizacji aplikacji.

> [!NOTE]
> W tym podejściu przyjęto założenie, że aplikacja dostosowuje wysokość, Szerokość i położenie formantów automatycznie, aby pomieścić różne rozmiary ciągów tekstowych w różnych kulturach. Windows Forms zawiera rozmaite kontrolki i technologie umożliwiające zaprojektowanie formularza w celu ułatwienia jego lokalizowalności, w tym <xref:System.Windows.Forms.FlowLayoutPanel> formantów i <xref:System.Windows.Forms.TableLayoutPanel> kontrolek oraz <xref:System.Windows.Forms.Control.AutoSize%2A> właściwości.  Zobacz również [instrukcje: obsługa lokalizacji w formularzach systemu Windows przy użyciu funkcji AutoSize i formantu TableLayoutPanel](/previous-versions/visualstudio/visual-studio-2010/1zkt8b33(v=vs.100)).

## <a name="generate-one-deployment-for-each-culture"></a>Generuj jedno wdrożenie dla każdej kultury
 W tej strategii wdrażania generowane są wiele wdrożeń. W każdym wdrożeniu należy uwzględnić tylko zestaw satelicki, który jest wymagany dla określonej kultury, i oznaczyć wdrożenie jako specyficzne dla tej kultury.

 Aby użyć tej metody w programie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , należy ustawić właściwość **Publikowanie języka** na karcie **Publikowanie** na żądany region. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] spowoduje automatyczne uwzględnienie zestawu satelickiego wymaganego w wybranym regionie i wykluczenie wszystkich innych zestawów satelickich z wdrożenia.

 Tę samą czynność można wykonać za pomocą narzędzia *MageUI.exe* w firmie Microsoft [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] . Użyj przycisku **Wypełnij** na karcie **pliki** manifestu aplikacji, aby wykluczyć wszystkie inne zestawy satelickie z katalogu aplikacji, a następnie ustaw pole **kultura** na karcie **Nazwa** manifestu wdrożenia w *MageUI.exe*. Te kroki nie tylko zawierają prawidłowy zestaw satelicki, ale również ustawiają `language` atrybut dla `assemblyIdentity` elementu w manifeście wdrożenia do odpowiedniej kultury.

 Po opublikowaniu aplikacji należy powtórzyć ten krok dla każdej dodatkowej kultury obsługiwanej przez aplikację. Musisz się upewnić, że publikujesz w innym katalogu serwera sieci Web lub katalogu udziału plików za każdym razem, ponieważ każdy manifest aplikacji odwołuje się do innego zestawu satelickiego, a każdy manifest wdrożenia będzie miał inną wartość dla `language` atrybutu.

## <a name="download-satellite-assemblies-on-demand"></a>Pobieranie zestawów satelickich na żądanie
 Jeśli zdecydujesz się na uwzględnienie wszystkich zestawów satelickich w jednym wdrożeniu, można zwiększyć wydajność przy użyciu pobierania na żądanie, co pozwala na oznaczenie zestawów jako opcjonalnych. Oznaczone zestawy nie będą pobierane, gdy aplikacja zostanie zainstalowana lub zaktualizowana. Zestawy można zainstalować, gdy są potrzebne, wywołując <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A> metodę w <xref:System.Deployment.Application.ApplicationDeployment> klasie.

 Pobieranie zestawów satelickich na żądanie różni się nieco od pobrania innych typów zestawów na żądanie. Aby uzyskać więcej informacji i przykłady kodu na temat sposobu włączania tego scenariusza przy użyciu [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] narzędzi dla programu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , zobacz [Przewodnik: pobieranie zestawów satelickich na żądanie przy użyciu interfejsu API wdrażania ClickOnce](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md).

 W programie można również włączyć ten scenariusz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .  Zobacz również [Przewodnik: pobieranie zestawów satelickich na żądanie za pomocą interfejsu API wdrażania ClickOnce przy użyciu narzędzia Projektant](/previous-versions/visualstudio/visual-studio-2012/ms366788(v=vs.110)) lub [Przewodnik: pobieranie zestawów satelickich na żądanie za pomocą interfejsu API wdrażania ClickOnce przy użyciu narzędzia Projektant](/previous-versions/visualstudio/visual-studio-2013/ms366788(v=vs.120)).

## <a name="testing-localized-clickonce-applications-before-deployment"></a>Testowanie zlokalizowanych aplikacji ClickOnce przed wdrożeniem
 Zestaw satelicki zostanie użyty dla aplikacji Windows Forms tylko wtedy, gdy <xref:System.Threading.Thread.CurrentUICulture%2A> Właściwość głównego wątku aplikacji jest ustawiona na kulturę zestawu satelickiego. Klienci na rynkach lokalnych prawdopodobnie mają już uruchomioną zlokalizowaną wersję systemu Windows z ustawionym kulturą.

 Dostępne są trzy opcje testowania zlokalizowanych wdrożeń przed udostępnieniem aplikacji klientom:

- Aplikację można uruchomić [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] w odpowiednich zlokalizowanych wersjach systemu Windows.

- Właściwość można ustawić <xref:System.Threading.Thread.CurrentUICulture%2A> programowo w aplikacji. (Ta właściwość musi być ustawiona przed wywołaniem <xref:System.Windows.Forms.Application.Run%2A> metody).

## <a name="see-also"></a>Zobacz też
- [\<assemblyIdentity> postaci](../deployment/assemblyidentity-element-clickonce-deployment.md)
- [Zabezpieczenia i wdrażanie technologii ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Globalizacja formularzy systemu Windows](/dotnet/framework/winforms/advanced/globalizing-windows-forms)