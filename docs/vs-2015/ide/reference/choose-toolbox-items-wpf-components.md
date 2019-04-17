---
title: Wybierz elementy paska narzędzi, składniki WPF | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.chooseitems.wpfcomponents
helpviewer_keywords:
- WPF Components tab, Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box, WPF Components tab
ms.assetid: 6ce1d178-88c0-4295-8915-59fdeedabb11
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4cbfaea72633f6f4bbeb7da3bf6e7c02069889f9
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59647705"
---
# <a name="choose-toolbox-items-wpf-components"></a>Wybierz elementy paska narzędzi, składniki WPF
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ta karta **wybierz elementy przybornika** okno dialogowe wyświetla listę formantów Windows Presentation Foundation (WPF), które są dostępne na komputerze lokalnym. Do wyświetlania tej listy, wybierz **wybierz elementy przybornika** z **narzędzia** menu, aby wyświetlić **wybierz elementy przybornika** okno dialogowe, a następnie wybierz jego **WPF Składniki** kartę. Aby posortować składniki na liście, wybierz nagłówek dowolnej kolumny.  
  
- Gdy zaznaczone jest pole wyboru obok składnika, ikona tych składników, będą wyświetlane w **przybornika**.  
  
  > [!TIP]
  >  Aby dodać wystąpienie kontrolki WPF do projektu dokument otwarty do edycji, przeciągnij jego **przybornika** ikony na powierzchnię projektową widoku. Domyślne znaczników i kodu dla składnika są wstawiane do projektu, możesz zmodyfikować. Aby uzyskać więcej informacji, zobacz [jak: Zarządzanie oknem przybornika](http://msdn.microsoft.com/a022c3fe-298c-4a59-a48f-b050da90ebc2) i [jak: Karty przybornika manipulowania](http://msdn.microsoft.com/21285050-cadd-455a-b1f5-a2289a89c4db).  
  
- Po wyczyszczeniu pola wyboru obok składnika odpowiednią ikonę zostaną usunięte z **przybornika.**  
  
  > [!NOTE]
  >  Składniki .NET Framework zainstalowana na danym komputerze pozostaną dostępne, czy ich ikony są wyświetlane w **przybornika**.  
  
  Kolumny na **składniki WPF** karta zawiera następujące informacje:  
  
  Nazwa  
  Wyświetla listę nazw kontrolek WPF, dla których wpisy znajdują się w rejestrze na komputerze.  
  
  Przestrzeń nazw  
  Wyświetla hierarchię [NIB: Biblioteka klas programu .NET Framework](http://msdn.microsoft.com/6c4f3a62-6a0f-41f2-9d52-ee0b13686f29) przestrzeni nazw, który definiuje strukturę składnika. Sortuj w tej kolumnie, aby wyświetlić listę dostępnych składników w każdej przestrzeni nazw z .NET Framework zainstalowana na danym komputerze.  
  
  Nazwa zestawu  
  Wyświetla nazwę zestawu .NET Framework, który zawiera przestrzeń nazw dla każdego składnika. Sortuj od tej kolumny, aby wyświetlić listę przestrzeni nazw zawartych w każdym zestawie .NET Framework zainstalowana na danym komputerze.  
  
  Katalog  
  Wyświetla lokalizację zestawu .NET Framework. Domyślna lokalizacja dla wszystkich zestawów to Global Assembly Cache. Aby uzyskać więcej informacji na temat globalnej pamięci podręcznej zestawów, zobacz [Praca z zestawami i Global Assembly Cache](http://msdn.microsoft.com/library/8a18e5c2-d41d-49ef-abcb-7c27e2469433).  
  
## <a name="uielement-list"></a>Lista elementów UI  
 **Filtr**  
 Filtruje listę kontrolek WPF, w oparciu o ciąg, który należy podać w polu tekstowym. Wyświetlane są wszystkie dopasowania z dowolnego z czterech kolumn.  
  
 **Usuń zaznaczenie**  
 Czyści ciągu filtru.  
  
 **Przeglądaj**  
 Otwiera **Otwórz** okno dialogowe, które umożliwia przejście do zespołów, które zawierają formanty WPF. Umożliwia ładowanie zestawów, które nie znajdują się w globalnej pamięci podręcznej zestawów.  
  
 **Język**  
 Pokazuje zlokalizowanego języka zestawu, który zawiera wybranej kontrolki WPF.  
  
## <a name="limitations"></a>Ograniczenia  
 Dodawanie niestandardowego formantu lub <xref:System.Windows.Controls.UserControl> do przybornika ma następujące ograniczenia.  
  
- Działa tylko w przypadku kontrolek niestandardowych, zdefiniowanych poza bieżącym projekcie.  
  
- Nie jest aktualizowany poprawnie po zmianie konfiguracji rozwiązania z debugowania na wydanie lub wersja do debugowania. Jest to spowodowane odwołania nie jest odwołanie do projektu, ale zamiast tego jest dla zestawu na dysku. Jeśli kontrolka jest częścią bieżącego rozwiązania, gdy zmienią się z poziomu pozycji Debuguj wydania, projekt w dalszym ciągu odwoływać się do kontroli wersji do debugowania.  
  
  Ponadto, jeśli metadanych w czasie projektowania jest stosowany do formantu niestandardowego i metadane Określa, że <xref:Microsoft.Windows.Design.ToolboxBrowsableAttribute> ustawiono `false`, formant nie jest wyświetlana w przyborniku.  
  
  Możesz odwoływać się kontrolkom bezpośrednio w widoku XAML przez mapowanie przestrzeni nazw i zestawu dla formantu. Aby uzyskać więcej informacji, zobacz [jak: Importowanie Namespace XAML](http://msdn.microsoft.com/6cda7c7a-369c-47dd-9c2d-13a35dcf737c).  
  
## <a name="see-also"></a>Zobacz też  
 [Wybierz elementy przybornika, okno dialogowe (Visual Studio)](http://msdn.microsoft.com/bd07835f-18a8-433e-bccc-7141f65263bb)   
 [Przybornik](../../ide/reference/toolbox.md)   
 [Instrukcje: Użyj kontrolki WPF innych firm w aplikacji WPF](http://msdn.microsoft.com/f4c0b601-3818-4f9f-85e5-77905f3b427f)   
 [Projektant WPF](http://msdn.microsoft.com/c6c65214-8411-4e16-b254-163ed4099c26)
