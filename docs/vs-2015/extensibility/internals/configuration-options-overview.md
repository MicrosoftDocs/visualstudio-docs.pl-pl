---
title: Opcje konfiguracji — Przegląd | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project configurations
- configuration options, about configuration options
ms.assetid: f4ad4dd3-b39e-42df-ad89-d403cdf24a2b
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0b37d93adbd2accb7a12fb176ab15aafc6914190
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441514"
---
# <a name="configuration-options-overview"></a>Omówienie opcji konfiguracji
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Projekty w [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] może obsługiwać wiele konfiguracji, które może być kompilowana, debugowania, wykonywania i/lub wdrożone. Konfiguracja jest opisane nazwany zestaw właściwości, zwykle przełączniki kompilatora i lokalizacje plików typu kompilacji. Domyślnie nowe rozwiązania zawiera dwie konfiguracje Debug i Release. Te konfiguracje mogą być stosowane przy użyciu ustawień domyślnych lub zmodyfikowane w celu spełnienia określonych wymagań rozwiązania lub projektu. Niektóre pakiety można tworzyć na dwa sposoby: jako edytora ActiveX lub jako składnik w miejscu. Projekty nie trzeba jednak obsługuje wiele konfiguracji. Jeśli jest dostępna tylko w jednej konfiguracji, że konfiguracja jest mapowany do wszystkich konfiguracji rozwiązania.  
  
 Konfiguracje zwykle składają się z dwóch części — Nazwa konfiguracji, (takie jak Debuguj lub Uwolnij) i ustawienia platformy. Nazwa platformy konfiguracji identyfikuje środowisko, które elementy docelowe konfiguracji, takich jak interfejs API zestawu lub platformy systemu operacyjnego. Użytkownicy [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] nie można utworzyć platformy; musi wybrać z opcji projektu pakietu VSPackage umożliwia. Podczas instalacji przez użytkownika pakietu VSPackage, platforma dostarczania utworzonych podczas opracowywania aplikacji pakietu może pojawiać się w dowolnej nazwy platformy desired na podstawie wszystkich kryteriów ustawione przez autora pakietu. Użytkownik może następnie wybrać z listy platform udostępniane się za pomocą pakietu VSPackage, gdy są tworzone na stronach właściwości.  
  
 Nazw platform są opcjonalne, ponieważ nie wszystkie projekty obsługuje koncepcji platform. Podczas konfiguracji brakuje nazwy platformy, ciąg "n/d" jest wyświetlany w interfejsie użytkownika.  
  
 Każde rozwiązanie ma swój własny zestaw konfiguracji, tylko jeden z nich może być aktywne w danym momencie. Konfiguracja rozwiązania to zbiór nie więcej niż jedną konfigurację z każdego projektu. Jest ustalenie "nie więcej niż" ze względu na możliwość wykluczanie projektów z konfiguracji rozwiązania. Użytkownicy mogą tworzyć własne konfiguracje niestandardowe rozwiązanie.  
  
 W poniższej tabeli przedstawiono typowe konfiguracje ustawień projektu. Wiersze są oznaczone etykietami z nazwami konfiguracji i kolumny z nazwami platformy.  
  
|Nazwa konfiguracji|Platform — Win32|Platform — Win64|  
|------------------------|----------------------|----------------------|  
|Debugowanie|\<Ustawienia systemu Win32 debugowania >|\<Ustawienia Win64 debugowania >|  
|Wydanie|\<Ustawienia systemu Win32 wydania >|\<Ustawienia Win64 wydania >|  
|MyConfig|Brak|\<Ustawienia MyConfig Win64 >|  
  
> [!NOTE]
> Nie można utworzyć konfiguracji rozwiązania "MyConfig", który nie obejmuje to platforma "Win32", chyba, że docelowa projektu nie obsługuje systemu Win32.  
  
 Zmiana aktywnej konfiguracji rozwiązania wybiera zestaw konfiguracje projektu, które są wbudowane, uruchamiania, debugowania lub wdrożone w ramach tego rozwiązania. Na przykład jeśli zmienisz konfigurację aktywngo rozwiązania z wersji do debugowania, wszystkie projekty w ramach tego rozwiązania automatycznie są tworzone za pomocą konfiguracji projektów wskazane w konfiguracji debugowania rozwiązania. Projektów są zwykle również konfiguracje debugowania o nazwie, chyba że użytkownik wprowadził ręczne zmiany w środowisku programu Configuration Manager.  
  
 Właściwości konfiguracji rozwiązania, które są przechowywane dla każdego projektu obejmują nazwę projektu, nazwa konfiguracji projektu, flagi, aby wskazać, czy do tworzenia lub wdrażania i nazwa platformy. Aby uzyskać więcej informacji, zobacz [konfiguracji rozwiązania](../../extensibility/internals/solution-configuration.md).  
  
 Użytkownik może wyświetlić i ustaw parametry konfiguracji rozwiązania, wybierając rozwiązania w hierarchii (Eksplorator rozwiązań) i otwieranie stron właściwości. Podobnie można wyświetlić i ustawić parametry konfiguracji projektu, wybierając projekt w Eksploratorze rozwiązań i otwieranie stron właściwości dla tego projektu.  
  
 Użytkownika można także utworzyć jeden projekt przy użyciu ustawienia konfiguracji wydania i wszystkie pozostałe przy użyciu ustawienia konfiguracji debugowania, jeśli to konieczne. Aby uzyskać więcej informacji, zobacz [Konfigurowanie projektu do kompilowania](../../extensibility/internals/project-configuration-for-building.md).  
  
 Na poniższym diagramie przedstawiono, jak są implementowane interfejsy, które obsługują konfiguracje rozwiązania i projektu:  
  
 ![Ilustracja dotycząca konfiguracji interfejsów](../../extensibility/internals/media/vsconfiginterfaces.gif "vsConfigInterfaces")  
Interfejsy konfiguracji  
  
 Kilka uwagi odnoszące się do poprzedniego diagramu:  
  
- `IDispatch` jest oznaczony jako opcjonalny w obiekcie konfiguracji. Ściślej mówiąc jest to opcjonalne mieć interfejsy konfiguracji w obiekcie przeglądania.  
  
- `IVsDebuggableProjectCfg` oznaczone jako opcjonalne w obiekt konfiguracji, ale jest wymagany do obsługi debugowania.  
  
- `IVsProjectCfg2` oznaczone jako opcjonalne w obiekt konfiguracji, ale wymagane jest grupowanie pomocy technicznej w danych wyjściowych.  
  
- `Config Provider` Obiekt jest oznaczony jako obiekt opcjonalne, ale ta opcja jest miejsce, do jej wdrożenia. Obiekt może wdrożyć na obiekt projektu lub na oddzielnym obiektem.  
  
- `IVsCfgProvider2` jest potrzebny do obsługi platformy i konfiguracji do edycji. `IVsCfgProvider` jest wystarczająca, jeśli nie należy implementować te funkcje.  
  
- Niektóre z tych obiektów, które przedstawiono na diagramie jako oddzielne obiekty mogą być połączone w tej samej klasy, gdzie jest to praktyczne zgodnie z wymaganiami określonego projektu. W innych tematach w tej sekcji jednak obiekty i interfejsy skojarzone z tymi obiektami zostanie dokładnie omówione zgodnie z scenariusz przedstawiony na diagramie.  
  
- Określone obiekty są implementowane oddzielnie. Na przykład projektu i tworzenia rozwiązań są dokonywane na oddzielnych wątkach i obiekt na potrzeby zarządzania życie kompilację oddzielnie od obiektu opisujący konfigurację kompilacji.  
  
  Aby uzyskać więcej informacji na obiekt konfiguracji w interfejsach i obiekt dostawcy konfiguracji na poprzednim rysunku, zobacz [obiekt konfiguracji projektu](../../extensibility/internals/project-configuration-object.md). Ponadto [Konfigurowanie projektu do kompilowania](../../extensibility/internals/project-configuration-for-building.md) zamieszczono więcej informacji dotyczących interfejsów konstruktora konfiguracji i tworzenie obiektu zależności i [konfiguracji projektu w celu wdrożenia zarządzania](../../extensibility/internals/project-configuration-for-managing-deployment.md) dalsze informacje interfejsów, dołączonych do narzędzia konfiguracji wdrażania i wdrożenie zależności obiektów. Na koniec [konfiguracji projektu dla danych wyjściowych](../../extensibility/internals/project-configuration-for-output.md) opisuje interfejsy grupy danych wyjściowych i obiekt danych wyjściowych i użycie stron właściwości, aby wyświetlić i ustaw właściwości konfiguracji-zależnych od ustawień lokalnych.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>   
 [Konfigurowanie projektu do kompilowania](../../extensibility/internals/project-configuration-for-building.md)   
 [Konfiguracja rozwiązania](../../extensibility/internals/solution-configuration.md)
