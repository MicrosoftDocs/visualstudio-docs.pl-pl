---
title: 'Przewodnik: pobieranie zestawów satelickich na żądanie przy użyciu interfejsu API wdrażania ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, globalization
- localization, Windows Forms
- Windows Forms, localization
- globalization, ClickOnce
- satellite assemblies, ClickOnce
- ClickOnce deployment, on-demand download
- localization, ClickOnce deployment
- ClickOnce deployment, localization
ms.assetid: fdaa553f-a27e-44eb-a4e2-08c122105a87
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a84de037661992d1ee185bea2a70db74dac5e618
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686354"
---
# <a name="walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api"></a>Wskazówki: pobieranie zestawów satelickich na żądanie przy użyciu wdrażania interfejsu API ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aplikacje Windows Forms można skonfigurować dla wielu kultur przy użyciu zestawów satelickich. *Zestaw satelicki* jest zestawem zawierającym zasoby aplikacji dla kultury innej niż domyślna kultura aplikacji.  
  
 Zgodnie z opisem w temacie [lokalizowanie aplikacji ClickOnce](../deployment/localizing-clickonce-applications.md)można uwzględnić wiele zestawów satelickich dla wielu kultur w ramach tego samego [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] wdrożenia. Domyślnie program [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] pobierze wszystkie zestawy satelickie we wdrożeniu na komputer kliencki, chociaż jeden klient prawdopodobnie będzie wymagał tylko jednego zestawu satelickiego.  
  
 W tym instruktażu przedstawiono sposób oznaczania zestawów satelickich jako opcjonalnych i pobrania tylko zestawu, który jest wymagany przez komputer kliencki dla bieżących ustawień kultury. Poniższa procedura zawiera narzędzia dostępne w narzędziu [!INCLUDE[winsdklong](../includes/winsdklong-md.md)] . To zadanie można także wykonać w temacie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  Zobacz również [Przewodnik: pobieranie zestawów satelickich na żądanie za pomocą interfejsu API wdrażania ClickOnce przy użyciu narzędzia Projektant](https://msdn.microsoft.com/library/ms366788\(v=vs.110\)) lub [Przewodnik: pobieranie zestawów satelickich na żądanie za pomocą interfejsu API wdrażania ClickOnce przy użyciu narzędzia Projektant](https://msdn.microsoft.com/library/ms366788\(v=vs.120\)).  
  
> [!NOTE]
> W celach testowych Poniższy przykładowy kod programowo ustawia kulturę na `ja-JP` . Zapoznaj się z sekcją "następne kroki" w dalszej części tego tematu, aby uzyskać informacje na temat dostosowywania tego kodu dla środowiska produkcyjnego.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym temacie założono, że wiesz, jak dodać zlokalizowane zasoby do aplikacji przy użyciu programu Visual Studio. Aby uzyskać szczegółowe instrukcje, zobacz [Przewodnik: lokalizowanie Windows Forms](https://msdn.microsoft.com/library/vstudio/y99d1cd3\(v=vs.100\).aspx).  
  
### <a name="to-download-satellite-assemblies-on-demand"></a>Pobieranie zestawów satelickich na żądanie  
  
1. Dodaj następujący kod do aplikacji, aby umożliwić pobieranie zestawów satelickich na żądanie.  
  
     [!code-csharp[ClickOnce.SatelliteAssembliesSDK#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnce.SatelliteAssembliesSDK/CS/Program.cs#1)]
     [!code-vb[ClickOnce.SatelliteAssembliesSDK#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnce.SatelliteAssembliesSDK/VB/Form1.vb#1)]  
  
2. Generowanie zestawów satelickich dla aplikacji przy użyciu [Resgen.exe (Generator plików zasobów)](https://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) lub [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
3. Wygeneruj manifest aplikacji lub Otwórz istniejący manifest aplikacji przy użyciu MageUI.exe. Aby uzyskać więcej informacji na temat tego narzędzia, zobacz [MageUI.exe (narzędzie tworzenia i edycji manifestów, klient graficzny)](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14).  
  
4. Kliknij kartę **pliki** .  
  
5. Kliknij przycisk **wielokropka** (**...**) i wybierz katalog zawierający wszystkie zestawy i pliki aplikacji, w tym zestawy satelickie, które zostały wygenerowane przy użyciu Resgen.exe. (Zestaw satelicki będzie miał nazwę w postaci *isoCode*\ApplicationName.resources.dll, gdzie *isoCode* jest identyfikatorem języka w formacie RFC 1766).  
  
6. Kliknij przycisk **Wypełnij** , aby dodać pliki do wdrożenia.  
  
7. Zaznacz pole wyboru **opcjonalne** dla każdego zestawu satelickiego.  
  
8. Ustaw pole grupy dla każdego zestawu satelickiego na jego identyfikator języka ISO. Na przykład dla japońskiego zestawu satelickiego należy określić nazwę grupy pobierania `ja-JP` . Spowoduje to włączenie kodu dodanego w kroku 1 w celu pobrania odpowiedniego zestawu satelickiego, w zależności od <xref:System.Threading.Thread.CurrentUICulture%2A> Ustawienia właściwości użytkownika.  
  
## <a name="next-steps"></a>Następne kroki  
 W środowisku produkcyjnym prawdopodobnie trzeba będzie usunąć wiersz w przykładowym kodzie, który <xref:System.Threading.Thread.CurrentUICulture%2A> ma ustawioną określoną wartość, ponieważ domyślnie maszyny klienckie będą mieć prawidłową wartość. Gdy aplikacja jest uruchamiana na japońskim komputerze klienckim, na przykład <xref:System.Threading.Thread.CurrentUICulture%2A> będzie `ja-JP` domyślnie. Ustawienie tej wartości programowo jest dobrym sposobem na testowanie zestawów satelickich przed wdrożeniem aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Lokalizowanie aplikacji ClickOnce](../deployment/localizing-clickonce-applications.md)
