---
layout: post
title: "Removendo acentos de uma string"
date: 2010-05-18 00:00:28 -0200
comments: true
categories: [C#, .NET]
author: Diogo Menezes
---

Cansamos de ver por ai, métodos que removem a acentuação de textos utilizando um número bem grande de replaces. Como por exemplo:

```
texto = texto.replace("À","A");
texto = texto.replace("á","a");
texto = texto.replace("é","e");
```

Apenas para ajudar os desavisados, criei um extension method em c# que remove a acentuação de uma string qualquer. Ele é mais elegante pois faz o processo de remoção de acentos utilizando recursos de [normalização de strings](http://msdn.microsoft.com/en-us/library/ebza6ck1.aspx).

```
public static class Extensao
{
	public static string RemoverAcentuacao(this string texto)
	{
		string semAcento = string.Empty;
		var letras = texto.Normalize(NormalizationForm.FormD).ToCharArray();
		foreach (char letra in letras)
			if (System.Globalization.CharUnicodeInfo.GetUnicodeCategory(letra) != System.Globalization.UnicodeCategory.NonSpacingMark)
				semAcento += letra;

		return semAcento;
	}
}
```

Para usar, basta chamá-lo em uma string qualquer como nos exemplos abaixo:

```
// assim...
string texto = "O Caminhão é vermelho";
string semAcento = texto.RemoverAcentuacao();

// ou simplesmente assim
var resultado = "O Caminhão é vermelho".RemoverAcentuacao();
```
