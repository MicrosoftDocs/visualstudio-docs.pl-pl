---
title: 'Przewodnik: Pobieranie zestawów satelickich na żądanie przy użyciu wdrażania ClickOnce interfejsu API przy użyciu narzędzia Projektant | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows Forms, globalization
- ClickOnce deployment, globalization
- localization, Windows Forms
- ClickOnce, on-demand download
- Windows Forms, localization
- ClickOnce deployment, localization
- walkthroughs, localization
ms.assetid: 82b85a47-b223-4221-a17c-38a52c3fb6e2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb3003ebf8fe102caac1dabfb4c87de521a57c77
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63405909"
---
# <a name="walkthrough-download-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer"></a>Przewodnik: Pobieranie zestawów satelickich na żądanie z wdrożeniem ClickOnce interfejsu API przy użyciu narzędzia Projektant
Aplikacje Windows Forms można skonfigurować dla wielu języków przy użyciu zestawów satelickich. A *zestawie satelickim* to zestaw, który zawiera zasoby aplikacji dla kultury innej niż aplikacja domyślna kultura.

 Zgodnie z opisem w [lokalizowanie aplikacji ClickOnce](../deployment/localizing-clickonce-applications.md), może zawierać wiele zestawów satelickich dla różnych kultur, w tym samym [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia. Domyślnie [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pobierze wszystkie zestawy satelickie w danym wdrożeniu na komputerze klienckim, mimo że pojedynczego klienta, prawdopodobnie będziesz potrzebować zestawu satelickiego tylko jeden.

 W tym instruktażu pokazano, jak oznaczyć swoje zestawy satelickie jako opcjonalne i Pobierz tylko zestaw na komputerze klienckim musi uzyskać bieżące ustawienia kultury.

> [!NOTE]
> Do celów testowych, w poniższych przykładach kodu programowo równa kulturę `ja-JP`. Zobacz sekcję "Kolejne kroki" w dalszej części tego tematu zawiera informacje na temat dostosować ten kod w środowisku produkcyjnym.

### <a name="to-mark-satellite-assemblies-as-optional"></a>Aby oznaczyć jako opcjonalne zestawy satelickie

1. Skompilowanie projektu. Spowoduje to wygenerowanie zestawów satelickich dla wszystkich kultur, w których lokalizujesz do.

2. Kliknij prawym przyciskiem myszy nazwę projektu w Eksploratorze rozwiązań, a następnie kliknij przycisk **właściwości**.

3. Kliknij przycisk **Publikuj** kartę, a następnie kliknij przycisk **pliki aplikacji**.

4. Wybierz **Pokaż wszystkie pliki** pole wyboru, aby wyświetlić zestawy satelickie. Domyślnie wszystkie zestawy satelickie zostaną uwzględnione we wdrożeniu i będą widoczne w tym oknie dialogowym.

     Zestawu satelickiego mają nazwy w postaci  *\<isoCode > \ApplicationName.resources.dll*, gdzie \<isoCode > jest w formacie RFC 1766 identyfikator języka.

5. Kliknij przycisk **New** w **grupa pobierania** listy dla każdego identyfikatora języka. Po wyświetleniu monitu Pobierz nazwę grupy, należy wprowadzić identyfikator języka. Na przykład dla zestawu satelickiego japońskiego, należy określić nazwę grupy pobierania `ja-JP`.

6. Zamknij **pliki aplikacji** okno dialogowe.

### <a name="to-download-satellite-assemblies-on-demand-in-c"></a>Aby pobrać zestawów satelickich na żądanie w języku C\#

1. Otwórz *Program.cs* pliku. Jeśli nie widzisz tego pliku w Eksploratorze rozwiązań, wybierz swój projekt, a na **projektu** menu, kliknij przycisk **Pokaż wszystkie pliki**.

2. Użyj poniższego kodu, aby pobrać zestawu satelickiego odpowiednie i uruchomić aplikację.

     [!code-csharp[ClickOnce.SatelliteAssemblies#1](../deployment/codesnippet/CSharp/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_1.cs)]

### <a name="to-download-satellite-assemblies-on-demand-in-visual-basic"></a>Aby pobrać zestawów satelickich na żądanie w języku Visual Basic

1. W **właściwości** okna aplikacji, kliknij przycisk **aplikacji** kartę.

2. W dolnej części strony karty kliknij **Wyświetl zdarzenia aplikacji**.

3. Dodaj następujące instrukcje importu na początku *ApplicationEvents.VB* pliku.

     [!code-vb[ClickOnce.SatelliteAssembliesVB#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_2.vb)]

4. Dodaj następujący kod do `MyApplication` klasy.

     [!code-vb[ClickOnce.SatelliteAssembliesVB#2](../deployment/codesnippet/VisualBasic/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_3.vb)]

## <a name="next-steps"></a>Następne kroki
 W środowisku produkcyjnym prawdopodobnie konieczne będzie usunięcie wiersza w przykłady kodu, które ustawia <xref:System.Threading.Thread.CurrentUICulture%2A> na określoną wartość, ponieważ klient maszyny będą poprawną wartość ustawiono domyślnie. Gdy aplikacja działa na komputerze klienckim japońskiego, na przykład <xref:System.Threading.Thread.CurrentUICulture%2A> będzie `ja-JP` domyślnie. Ustawieniem dla niego programowe jest dobrym sposobem do testowania zestawów satelickich, przed wdrożeniem aplikacji.

## <a name="see-also"></a>Zobacz także
- [Przewodnik: Pobieranie zestawów satelickich na żądanie przy użyciu wdrażania interfejsu API ClickOnce](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md)
- [Lokalizowanie aplikacji ClickOnce](../deployment/localizing-clickonce-applications.md)
