---
title: Zarządzanie podpisywaniem zestawu i manifestu | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 98d764bae48fb7deaa3f3cf917b0d4c8baab185b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651366"
---
# <a name="managing-assembly-and-manifest-signing"></a>Zarządzanie zestawem i podpisywanie manifestu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podpisywanie silnej nazwy daje składnikowi oprogramowania unikatowy identyfikator globalny. Silne nazwy są używane w celu zagwarantowania, że zestaw nie może być sfałszowany przez kogoś innego, i aby upewnić się, że zależności składników i instrukcje konfiguracji są mapowane na poprawną wersję składnika i składnika.

 Silna nazwa składa się z tożsamości zestawu (prostej nazwy tekstu, numeru wersji i informacji o kulturze) oraz tokenu klucza publicznego i podpisu cyfrowego.

 Aby uzyskać informacje na temat podpisywania zestawów w projektach Visual Basic i C#, zobacz [Tworzenie i używanie zestawów o silnej nazwie](https://msdn.microsoft.com/library/ffbf6d9e-4a88-4a8a-9645-4ce0ee1ee5f9).

 Aby uzyskać informacje na temat podpisywania zestawów w projektach Visual C++, zobacz [zestawy o silnych nazwach (podpisywanie zestawów) (C++/CLI)](https://msdn.microsoft.com/library/c337cd3f-e5dd-4c6f-a1ad-437e85dba1cc).

## <a name="asset-types-and-signing"></a>Typy zasobów i podpisywanie
 Można podpisywać zestawy .NET i manifesty aplikacji. Należą do nich następujące funkcje:

- Pliki wykonywalne (. exe)

- manifesty aplikacji (. exe. manifest)

- manifesty wdrożenia (. Application)

- współużytkowane zestawy składników (. dll)

  Należy podpisać następujące typy zasobów:

1. Zestawy, które mają zostać wdrożone w globalnej pamięci podręcznej zestawów (GAC).

2. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifesty aplikacji i wdrażania. Program Visual Studio umożliwia podpisywanie domyślnie dla tych aplikacji.

3. Podstawowe zestawy międzyoperacyjności, które są używane na potrzeby współdziałania modelu COM. Narzędzie TLBIMP wymusza silne nazewnictwo podczas tworzenia podstawowego zestawu międzyoperacyjnego na podstawie biblioteki typów modelu COM.

   Ogólnie rzecz biorąc nie należy podpisywać plików wykonywalnych. Składnik o silnej nazwie nie może odwoływać się do niesilnie nazwanego składnika wdrożonego z aplikacją. Program Visual Studio nie podpisuje plików wykonywalnych aplikacji, ale zamiast tego rejestruje manifest aplikacji, który wskazuje na plik wykonywalny o słabym kodzie. Zwykle należy unikać podpisywania składników, które są prywatne dla aplikacji, ponieważ podpisywanie może utrudniać zarządzanie zależnościami.

## <a name="how-to-sign-an-assembly-in-visual-studio"></a>Jak podpisać zestaw w programie Visual Studio
 Możesz podpisać aplikację lub składnik przy użyciu karty **podpisywanie** okna właściwości projektu (kliknij prawym przyciskiem myszy węzeł projektu w **Eksplorator rozwiązań** i wybierz **Właściwości**lub wpisz **właściwości projektu** w oknie **Szybkie uruchamianie** lub naciśnij klawisze ALT + ENTER wewnątrz okna **Eksplorator rozwiązań** ). Wybierz kartę **podpisywanie** , a następnie zaznacz pole wyboru **podpisz zestaw**  .

 Określ plik klucza. Jeśli wybierzesz opcję utworzenia nowego pliku klucza, należy pamiętać, że nowe pliki kluczy są zawsze tworzone w formacie PFX. Musisz mieć nazwę i hasło dla nowego pliku.

> [!WARNING]
> Należy zawsze chronić plik klucza przy użyciu hasła, aby uniemożliwić innym osobom korzystanie z niego. Klucze można także zabezpieczyć za pomocą dostawców lub magazynów certyfikatów.

 Możesz również wskazać klucz, który został już utworzony. Aby uzyskać więcej informacji na temat tworzenia kluczy, zobacz [How to: Create a Public-Private Key para](https://msdn.microsoft.com/library/05026813-f3bd-4d7c-9e0b-fc588eb3d114).

 Jeśli masz dostęp tylko do klucza publicznego, możesz użyć podpisywania opóźnień, aby odroczyć przypisanie klucza. Aby włączyć podpisywanie opóźnień, należy zaznaczyć pole wyboru **Opóźnij tylko znak** . Projekt podpisany z opóźnieniem nie zostanie uruchomiony i nie będzie można go debugować. Można jednak pominąć weryfikację podczas opracowywania przy użyciu [Sn.exe (narzędzia silnej nazwy)](https://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6) z `-Vr` opcją.

 Informacje o podpisywaniu manifestów znajdują się w temacie [How to: Signing Application and Deployment Manifests](../ide/how-to-sign-application-and-deployment-manifests.md).

## <a name="see-also"></a>Zobacz też
 Zestawy [o silnej nazwie zestawy o](https://msdn.microsoft.com/library/d4a80263-f3e0-4d81-9b61-f0cbeae3797b) silnych [nazwach (podpisywanie zestawów) (C++/CLI)](https://msdn.microsoft.com/library/c337cd3f-e5dd-4c6f-a1ad-437e85dba1cc)
