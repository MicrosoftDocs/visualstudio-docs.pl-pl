---
title: Shell (Isolated lub Integrated) | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 9d8b08dfe812245a21160fa2f16b4c94728785ae
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54792572"
---
# <a name="shell-isolated-or-integrated"></a>Shell (Isolated lub Integrated)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można utworzyć własną aplikację na podstawie programu Visual Studio w trybie zintegrowanym lub izolowanych. W trybie zintegrowanym wiele funkcji programu Visual Studio dostępnych dodatkowo oprócz używanej aplikacji. W trybie izolowanym wybierasz podzbiór funkcji programu Visual Studio, które chcesz rozpowszechnić razem ze swoim rozszerzeniem.  
  
## <a name="integrated-mode"></a>W trybie zintegrowanym  
 W trybie zintegrowanym użytkownikom użyć standardowych funkcji programu Visual Studio wraz z Twojego niestandardowego narzędzia. Integrated shell jest przeznaczony głównie do obsługi języków programowania i narzędzi do tworzenia oprogramowania.  
  
 Narzędzia niestandardowe, które są tworzone automatycznie na integrated shell scalić z innej wersji programu Visual Studio, który jest zainstalowany na tym samym komputerze. Możesz podać wersji redystrybucyjnej powłoki programu Visual Studio, jeśli nie zainstalowano jeszcze programu Visual Studio.  
  
 Powłoka programu Visual Studio w wersji redystrybucyjnej nie obejmuje programowania języków i funkcji, które obsługują swoich systemów odpowiednich projektu.  
  
> [!NOTE]
>  Tryb zintegrowany programu Visual Studio shell można zainstalować razem z wszystkich wersji programu Visual Studio, z wyjątkiem wersji Express.  
  
 Aby uzyskać więcej informacji, zobacz [programu Visual Studio Shell (zintegrowany)](../extensibility/visual-studio-shell-integrated.md).  
  
## <a name="isolated-mode"></a>Tryb izolowany  
 Tryb izolowany pozwala tworzyć narzędzia niestandardowe, które są uruchamiane side-by-side z innymi wersjami programu Visual Studio. Jest ona przeznaczona głównie do narzędzia, które mieli dostęp do usług Visual Studio bez zależności ze standardowych funkcji programu Visual Studio. Można dostosować wygląd aplikacji utworzonych na powłoki programu Visual Studio, izolowany. Łatwo można wyłączyć funkcji i grup poleceń menu, które nie mają być wyświetlane wraz z aplikacją.  
  
 Aby uzyskać więcej informacji, zobacz [Visual Studio Isolated Shell](../extensibility/visual-studio-isolated-shell.md).  
  
## <a name="distributing-your-integrated-or-isolated-shell-application"></a>Dystrybuowanie aplikacji zintegrowanych lub izolowane powłoki  
 Do dystrybucji własnej aplikacji zintegrowanych lub izolowane powłoki, należy dołączyć aplikację, specjalne lub odizolowane w zintegrowanym powłokę pakiet redystrybucyjny i program instalacyjny. Aby uzyskać więcej informacji na temat dystrybucją i instalacją, zobacz [dystrybucja aplikacje izolowane powłoki](../extensibility/distributing-isolated-shell-applications.md).  
  
> [!IMPORTANT]
>  [Umowy licencyjnej użytkownika końcowego (EULA)](https://www.visualstudio.com/support/legal/mt171552) dla programu Visual Studio integrated i isolated powłoki zawiera sekcję zbierania danych (**sekcja 3. Dane**).  Opisano w nim dane użycia klienta, które mogą być zbierane przez firmę Microsoft od użytkowników albo zintegrowane lub izolowane powłoki oprogramowania, które umieszczenie w aplikacji. Aby uzyskać więcej informacji, zobacz [programu Microsoft Visual Studio zachowania poufności rodziny produktów](https://www.visualstudio.com/dn948229).  
> 
>  W przypadku zbierania danych użycia osobnych od klientów za pośrednictwem aplikacji, musisz podać odpowiednie powiadomienie użytkowników aplikacji można zebrać.  Podczas dystrybucji oprogramowania powłoki izolowanej i zintegrowanej jako część aplikacji, zgodnie z licencji programu Visual Studio Software Development Kit, musi zawierać jedną z następujących czynności:  
> 
> - Umowa licencyjna użytkownika w ramach licencji na aplikację  
>   -   własne umowy licencyjnej, wymagającego klienci musieli się zgodzić na warunki, które chronią programu Visual Studio integrated lub isolated shell co najmniej taką ilość jako użytkownik końcowy postanowień licencyjnych firmy Microsoft oprogramowanie powłoki  
  
## <a name="additional-resources"></a>Dodatkowe zasoby  
 Aby uzyskać więcej informacji na temat pakietów redystrybucyjnych zobacz [pobieranie Visual Studio Extensibility](http://go.microsoft.com/fwlink/?LinkID=119298) witryny sieci Web.  
  
## <a name="see-also"></a>Zobacz też  
 [Dostarczanie rozszerzeń programu Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
