---
title: Zarządzanie podpisywaniem zestawu i manifestu | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- manifests [Visual Studio]
- signing manifests [Visual Studio]
- application manifests [Visual Studio]
- assemblies [Visual Studio], signing
ms.assetid: 6c1ef36b-25f7-4ad0-b29a-51801b7a5420
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d3f842d45df1525cb3f736019eeec52dd65b67aa
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443738"
---
# <a name="managing-assembly-and-manifest-signing"></a>Zarządzanie zestawem i podpisywanie manifestu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podpisywania silnymi zawiera składnik oprogramowania globalnie unikatową tożsamość. Silne nazwy są używane w celu zagwarantowania, że zestaw nie sfałszowane przez kogoś innego i upewnij się, że składnika, zależności i instrukcji konfiguracji mapowania na poprawne składnik, a wersja składnika.  
  
 Silna nazwa składa się z tożsamości zestawu (nazwa prosty tekst, numeru wersji i informacji o kulturze) oraz token klucza publicznego i podpisu cyfrowego.  
  
 Aby uzyskać informacje na temat podpisywania zestawów w projektach Visual Basic i C#, zobacz [tworzenie i zestawy Using Strong-Named](http://msdn.microsoft.com/library/ffbf6d9e-4a88-4a8a-9645-4ce0ee1ee5f9).  
  
 Dla informacji na temat podpisywania zestawów w elemencie wizualnym C++ projektów, zobacz [zestawy o silnej nazwach (podpisywanie zestawów) (C++sposób niezamierzony)](http://msdn.microsoft.com/library/c337cd3f-e5dd-4c6f-a1ad-437e85dba1cc).  
  
## <a name="asset-types-and-signing"></a>Typy zasobów i podpisywania  
 Można podpisać manifesty aplikacji i zestawy .NET. Należą do nich między innymi:  
  
- pliki wykonywalne (.exe)  
  
- Manifesty aplikacji (. exe.manifest)  
  
- manifesty wdrożenia (.application)  
  
- współużytkowany składnik zestawy (.dll)  
  
  Musisz zalogować się następujące typy zasobów:  
  
1. Zestawy, jeśli chcesz wdrożyć je w globalnej pamięci podręcznej zestawów (GAC).  
  
2. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Manifesty aplikacji i wdrożenia. Program Visual Studio umożliwia podpisywania domyślnie w przypadku tych aplikacji.  
  
3. Podstawowe zestawy międzyoperacyjne, które są używane do współdziałania COM. Narzędzia TLBIMP wymusza silne nazwy podczas tworzenia podstawowego zestawu międzyoperacyjnego z biblioteki typów COM.  
  
   Ogólnie rzecz biorąc nie powinien utworzyć pliki wykonywalne. Składnik silnej nazwy nie mogą odwoływać się bez — nazwie składnik wdrożoną wraz z aplikacją. Visual Studio nie podpisuje plików wykonywalnych aplikacji, ale zamiast tego podpisuje manifest aplikacji, które wskazuje do pliku wykonywalnego o nazwie weak. Ogólnie należy unikać podpisywania składników, które są prywatne do aplikacji, ponieważ podpisywanie może utrudnić zarządzanie zależnościami.  
  
## <a name="how-to-sign-an-assembly-in-visual-studio"></a>Jak zarejestrować zestaw w programie Visual Studio  
 Podpisywania aplikacji lub składnika przy użyciu **podpisywanie** karty w oknie właściwości projektu (kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań** i wybierz **właściwości**, lub typu **właściwości projektu** w **Szybkie uruchamianie** okna, naciśnij klawisze ALT + ENTER w **Eksploratora rozwiązań** okna). Wybierz **podpisywanie** kartę, a następnie wybierz **Podpisz zestaw** pole wyboru.  
  
 Określ plik klucza. Jeśli zdecydujesz się utworzyć nowy plik klucza, należy pamiętać, że zawsze zostaną utworzone nowe pliki klucza w formacie pfx. Należy nazwę i hasło dla nowego pliku.  
  
> [!WARNING]
> Zawsze należy chronić Twojego pliku klucza o hasło, aby uniemożliwić korzystanie z jej przez kogoś innego. Możesz również klucze można zabezpieczyć przy użyciu dostawców lub magazynów certyfikatów.  
  
 Możesz też wskazać w kluczu już utworzony. Aby uzyskać więcej informacji na temat tworzenia kluczy, zobacz [jak: Tworzenie pary kluczy publiczny prywatny](http://msdn.microsoft.com/library/05026813-f3bd-4d7c-9e0b-fc588eb3d114).  
  
 Jeśli masz dostęp tylko klucz publiczny, można użyć opóźnione podpisywanie mają być odroczone przypisywanie klucza. Włączanie opóźnione podpisywanie, wybierając **opóźnienie logowania tylko** pole wyboru. Projekt podpisywane z opóźnieniem nie będzie działać i nie można go debugować. Jednakże, możesz pominąć weryfikacji podczas programowania przy użyciu [Sn.exe (narzędzie silnych nazw)](http://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6) z `-Vr` opcji.  
  
 Aby uzyskać informacje dotyczące podpisywania manifestów, zobacz [jak: Podpisywanie aplikacji i manifestów wdrożenia](../ide/how-to-sign-application-and-deployment-manifests.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zestawy o silnych nazwach](http://msdn.microsoft.com/library/d4a80263-f3e0-4d81-9b61-f0cbeae3797b)   
 [Zestawy o silnych nazwach (podpisywanie zestawów) (C++/CLI)](http://msdn.microsoft.com/library/c337cd3f-e5dd-4c6f-a1ad-437e85dba1cc)
