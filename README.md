import React, { useState } from 'react';
import { StyleSheet, Text, TextInput, View, Button, TouchableOpacity } from 'react-native';


const getSaudacao = () => {
  const hour = new Date().getHours();
  if (hour >= 5 && hour < 12) return 'Bom dia';
  if (hour >= 12 && hour < 18) return 'Boa tarde';
  return 'Boa noite';
};

export default function App() {
  const [nome, setNome] = useState('');
  const [saudacao, setSaudacao] = useState('');
  

  const atualizarSaudacao = () => {
    if (nome.trim() !== '') {
      const saudacaoAtual = `${getSaudacao()}, ${nome}!`;
      setSaudacao(saudacaoAtual);
    }
  };


  const limparCampos = () => {
    setNome('');
    setSaudacao('');
  };

  return (
    <View style={styles.container}>
      <Text style={styles.titulo}>Saudação Personalizada</Text>
      
      <TextInput
        style={styles.input}
        placeholder="Digite seu nome"
        value={nome}
        onChangeText={setNome}
      />
      
      <TouchableOpacity style={styles.botao} onPress={atualizarSaudacao}>
        <Text style={styles.botaoTexto}>Atualizar Saudação</Text>
      </TouchableOpacity>

      {saudacao ? (
        <Text style={styles.saudacao}>{saudacao}</Text>
      ) : null}

      <TouchableOpacity style={styles.botaoLimpar} onPress={limparCampos}>
        <Text style={styles.botaoTexto}>Limpar</Text>
      </TouchableOpacity>
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
    backgroundColor: 'pink',
    padding: 20,
  },
  titulo: {
    fontSize: 24,
    fontWeight: 'bold',
    marginBottom: 20,
    color: 'green',
  },
  input: {
    width: '80%',
    height: 40,
    borderColor: 'gray',
    borderWidth: 1,
    borderRadius: 5,
    paddingHorizontal: 10,
    marginBottom: 20,
    fontSize: 18,
    backgroundColor: 'brown',
  },
  botao: {
    backgroundColor: 'green',
    padding: 10,
    borderRadius: 5,
    marginBottom: 10,
  },
  botaoLimpar: {
    backgroundColor: 'red',
    padding: 10,
    borderRadius: 5,
  },
  botaoTexto: {
    color: 'white',
    fontSize: 16,
    textAlign: 'center',
  },
  saudacao: {
    fontSize: 20,
    fontWeight: 'bold',
    color: 'orange',
    marginBottom: 20,
  },
});
