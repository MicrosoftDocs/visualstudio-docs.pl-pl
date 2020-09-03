---
title: Powłoka (izolowana lub zintegrowana) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell
- Visual Studio, Shell
- Shell [Visual Studio]
- Visual Studio shell, shell-based applications
- Shell [Visual Studio], shell-based applications
ms.assetid: c64a9bf0-9bf8-45c3-8fa2-306fa6cab66a
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: aa346ebfe321e4672ea3fa71a4dcc872ebf22cda
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850233"
---
# <a name="shell-isolated-or-integrated"></a>Shell (izolowany lub zintegrowany)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz utworzyć własną aplikację opartą na programie Visual Studio w trybie zintegrowanym lub izolowanym. W trybie zintegrowanym oprócz aplikacji dostępne są wiele funkcji programu Visual Studio. W trybie izolowanym wybierasz podzbiór funkcji programu Visual Studio, które chcesz dystrybuować wraz z własnymi rozszerzeniami.  
  
## <a name="integrated-mode"></a>Tryb zintegrowany  
 Tryb zintegrowany umożliwia użytkownikom używanie standardowych funkcji programu Visual Studio wraz z narzędziami niestandardowymi. Zintegrowana powłoka jest przeznaczona głównie do obsługi języków programowania i narzędzi programistycznych oprogramowania.  
  
 Narzędzia niestandardowe, które są oparte na zintegrowanej powłoce, są automatycznie scalane z dowolną inną wersją programu Visual Studio, która jest zainstalowana na tym samym komputerze. Jeśli program Visual Studio nie jest jeszcze zainstalowany, możesz udostępnić redystrybucyjną wersję powłoki zintegrowanej programu Visual Studio.  
  
 Pakiet redystrybucyjny zintegrowanej powłoki programu Visual Studio nie obejmuje języków programowania i funkcji obsługujących odpowiednie systemy projektów.  
  
> [!NOTE]
> Tryb zintegrowany programu Visual Studio Shell można zainstalować razem ze wszystkimi wersjami programu Visual Studio, z wyjątkiem wersji Express.  
  
 Aby uzyskać więcej informacji, zobacz [Visual Studio Shell (zintegrowany)](../extensibility/visual-studio-shell-integrated.md).  
  
## <a name="isolated-mode"></a>Tryb izolowany  
 Tryb izolowany umożliwia tworzenie niestandardowych narzędzi, które działają równolegle z innymi wersjami programu Visual Studio. Jest ona przeznaczona głównie dla narzędzi, które mogą uzyskać dostęp do usługi Visual Studio, bez w zależności od wszystkich standardowych funkcji programu Visual Studio. Można dostosować wygląd aplikacji skompilowanych w izolowanej powłoki programu Visual Studio. Możesz łatwo wyłączyć funkcje i grupy poleceń menu, które nie mają być wyświetlane razem z aplikacją.  
  
 Aby uzyskać więcej informacji, zobacz [izolowana powłoka programu Visual Studio](../extensibility/visual-studio-isolated-shell.md).  
  
## <a name="distributing-your-integrated-or-isolated-shell-application"></a>Dystrybuowanie aplikacji powłoki zintegrowanej lub izolowanej  
 W celu dystrybucji aplikacji powłoki zintegrowanej lub izolowanej należy uwzględnić aplikację, specjalny pakiet redystrybucyjny powłoki zintegrowanej lub izolowanej oraz program instalacyjny. Aby uzyskać więcej informacji na temat dystrybucji i instalacji, zobacz [dystrybuowanie izolowanych aplikacji powłoki](../extensibility/distributing-isolated-shell-applications.md).  
  
> [!IMPORTANT]
> [Umowa licencyjna użytkownika oprogramowania (EULA)](https://www.visualstudio.com/support/legal/mt171552) dla powłok zintegrowanych i izolowanych programu Visual Studio zawiera sekcję dotyczącą zbierania danych (**sekcja 3. Dane**).  Opisano w nim dane dotyczące użycia klienta, które mogą być zbierane przez firmę Microsoft od użytkowników zintegrowanego lub izolowanego oprogramowania powłoki, które można skompilować do aplikacji. Aby uzyskać więcej informacji, zobacz [Microsoft Visual Studio rodziny produktów zasady zachowania poufności](https://www.visualstudio.com/dn948229)informacji.  
> 
> Jeśli zbierasz oddzielne dane dotyczące użycia od klientów za pośrednictwem aplikacji, musisz podać odpowiednie powiadomienie dla użytkowników aplikacji, którą zbierasz.  W przypadku dystrybucji izolowanego lub zintegrowanego oprogramowania powłoki jako części aplikacji zgodnie z licencją programu Visual Studio Software Development Kit należy uwzględnić jedną z następujących czynności:  
> 
> - Umowa licencyjna użytkownika oprogramowania w ramach licencji aplikacji  
> - Twoja własna Umowa licencyjna użytkownika, która wymaga od klientów zgody na warunki chroniące powłokę programu Visual Studio Integrated lub izolowany, co najmniej tak samo, jak postanowienia licencyjne użytkowników końcowych firmy Microsoft dotyczące oprogramowania powłoki  
  
## <a name="additional-resources"></a>Dodatkowe zasoby  
 Aby uzyskać więcej informacji na temat pakietów redystrybucyjnych, zobacz witrynę sieci Web [do pobrania rozszerzalności programu Visual Studio](https://msdn.microsoft.com/vstudio/bb984878.aspx) .  
  
## <a name="see-also"></a>Zobacz też  
 [Dostarczanie rozszerzeń programu Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
