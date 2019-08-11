import React from 'react';
import { Text, View,Button ,TouchableOpacity,StyleSheet, TextInput} from 'react-native';
import { LinearGradient } from 'expo-linear-gradient';

export default class FacebookButton extends React.Component {
   constructor(props)
  {
    super(props)

      this.state = {
        num1:"",
        num2:"",
        dot:0,
        chack:0,
        chackOP:0,
        chackFOP:0,
        out:0,
        eiei:0,
        }
  }
  reset(){
     this.setState({num1:""});
     this.setState({num2:""});
     this.setState({dot:0});
     this.setState({chack:0});
     this.setState({chackOP:0});
     this.setState({chackFOP:0});
     this.setState({out:0});
     this.setState({eiei:0});

  }
  resetans(){
    this.setState({num1:""});
     this.setState({num2:""});
     this.setState({dot:0});
     this.setState({chack:0});
     this.setState({chackFOP:0});
     this.setState({eiei:0});
     this.setState({chackOP:0});
  }
  temp(num)
  {
    this.setState({chackFOP:1});
    if(this.state.chack==0){
      if(num=="." & this.state.dot==0){
        this.setState({num1:this.state.num1+num});
        this.setState({out:this.state.num1+num});
        this.setState({dot:this.state.dot+1});
      }
      else if(num=="." & this.state.dot>=0){
        this.setState({dot:this.state.dot+1});
      }
      else{
        this.setState({num1:this.state.num1+num});
        this.setState({out:this.state.num1+num});
      }
    }
    else if(this.state.chack==1){
      if(num=="." & this.state.dot==0){
        this.setState({num2:this.state.num2+num});
        this.setState({out:this.state.num2+num});
        this.setState({dot:this.state.dot+1});
      }
      else if(num=="." & this.state.dot!=0){
        this.setState({dot:this.state.dot+1});
      }
      else{
        this.setState({num2:this.state.num2+num});
        this.setState({out:this.state.num2+num});
      }
    }
  }
  op(x){
    if(x=="1" &this.state.chackOP==0 & this.state.chackFOP==1){
      this.setState({eiei:1});
      this.setState({chack:1});
      this.setState({chackOP:1});
      this.setState({dot:0});
      this.setState({out:"/"});
    }
    else if(x=="2" &this.state.chackOP==0 & this.state.chackFOP==1){
      this.setState({eiei:2});
      this.setState({chack:1});
      this.setState({chackOP:1});
      this.setState({dot:0});
      this.setState({out:"X"});
    }
    else if(x=="3" &this.state.chackOP==0 & this.state.chackFOP==1){
      this.setState({eiei:3});
      this.setState({chack:1});
      this.setState({chackOP:1});
      this.setState({dot:0});
      this.setState({out:"-"});
    }
    else if(x=="4" &this.state.chackOP==0 & this.state.chackFOP==1){
      this.setState({eiei:4});
      this.setState({chack:1});
      this.setState({chackOP:1});
      this.setState({dot:0});
      this.setState({out:"+"});
    }
  }
  ans(){
      var a = Number(this.state.num1)
      var b = Number(this.state.num2)
      if(this.state.eiei == 1){
        this.setState({out:a/b});
        this.resetans()    
      }
      else if(this.state.eiei == 2){
        this.setState({out:a*b}); 
        this.resetans()
      }
      else if(this.state.eiei == 3){
        this.setState({out:a-b});
        this.resetans()
      }
      else if(this.state.eiei == 4){
        this.setState({out:a+b}); 
        this.resetans()
      }
     else{
       this.setState({out:"Error"});
       this.resetans()
     }
  }
  render() {
    return (
        <LinearGradient
        colors={['#000000','#000000']}
        style={{flex: 1}}>
        <View style={{flex: 2}}>
        <Text style={styles.txtin}>{this.state.out}</Text>
        </View>
        <View style={{flex:1,flexDirection: 'row'}}>
          <TouchableOpacity style={styles.btn1} onPress = {()=>this.reset()}>
              <Text style={styles.txt2}>AC</Text>
          </TouchableOpacity>
          <TouchableOpacity style={styles.btn1}>
              <Text style={styles.txt2}>+/-</Text>
          </TouchableOpacity>
          <TouchableOpacity style={styles.btn1}>
              <Text style={styles.txt2}>%</Text>
          </TouchableOpacity>
          <TouchableOpacity style={styles.btn2} onPress = {()=>this.op(String(1))}>
              <Text style={styles.txt1}>/</Text>
          </TouchableOpacity>
        </View>
        <View style={{flex:1,flexDirection: 'row'}}>
          <TouchableOpacity style={styles.btn3} onPress = {()=>this.temp(String(7))}>
              <Text style={styles.txt1}>7</Text>
          </TouchableOpacity>
          <TouchableOpacity style={styles.btn3} onPress = {()=>this.temp(String(8))}>
              <Text style={styles.txt1}>8</Text>
          </TouchableOpacity>
          <TouchableOpacity style={styles.btn3} onPress = {()=>this.temp(String(9))}>
              <Text style={styles.txt1}>9</Text>
          </TouchableOpacity>
          <TouchableOpacity style={styles.btn2} onPress = {()=>this.op(String(2))}>
              <Text style={styles.txt1}>x</Text>
          </TouchableOpacity>
        </View> 
        <View style={{flex:1,flexDirection: 'row'}}>
          <TouchableOpacity style={styles.btn3} onPress = {()=>this.temp(String(4))}>
                <Text style={styles.txt1}>4</Text>
            </TouchableOpacity>
            <TouchableOpacity style={styles.btn3} onPress = {()=>this.temp(String(5))}>
                <Text style={styles.txt1}>5</Text>
            </TouchableOpacity>
            <TouchableOpacity style={styles.btn3} onPress = {()=>this.temp(String(6))}>
                <Text style={styles.txt1}>6</Text>
            </TouchableOpacity>
            <TouchableOpacity style={styles.btn2} onPress = {()=>this.op(String(3))} >
                <Text style={styles.txt1}>-</Text>
            </TouchableOpacity>
          </View> 
        <View style={{flex:1,flexDirection: 'row'}}>
        <TouchableOpacity style={styles.btn3} onPress = {()=>this.temp(String(1))}>
              <Text style={styles.txt1}>1</Text>
          </TouchableOpacity>
          <TouchableOpacity style={styles.btn3} onPress = {()=>this.temp(String(2))}>
              <Text style={styles.txt1}>2</Text>
          </TouchableOpacity>
          <TouchableOpacity style={styles.btn3} onPress = {()=>this.temp(String(3))}>
              <Text style={styles.txt1}>3</Text>
          </TouchableOpacity>
          <TouchableOpacity style={styles.btn2} onPress = {()=>this.op(String(4))} >
              <Text style={styles.txt1}>+</Text>
          </TouchableOpacity>
        </View> 
        <View style={{flex:1,flexDirection: 'row'}}>
          <TouchableOpacity style={styles.btn4} onPress = {()=>this.temp(String(0))} >
                <Text style={styles.txt4}>0</Text>
            </TouchableOpacity>
            <TouchableOpacity style={styles.btn3} onPress = {()=>this.temp(String("."))} >
                <Text style={styles.txt1}>.</Text>
            </TouchableOpacity>
            <TouchableOpacity style={styles.btn2} onPress = {()=>this.ans()}>
                <Text style={styles.txt1}>=</Text>
            </TouchableOpacity>
          </View> 
        </LinearGradient>
    );
  }
}
const styles = StyleSheet.create({
    txtin:{
      fontSize: 30,
      marginTop:30,
      height:"100%",
      marginLeft:"20px",
      color:'#ECF0F1'
    },
    btn1:{
        flex: 1,
        alignItems: 'center',
        backgroundColor: '#707B7C',
        borderRadius:"50%",
        margin:2,
        justifyContent: 'center'
    },
    btn2:{
        flex: 1,
        alignItems: 'center',
        backgroundColor: 'orange',
        borderRadius:"50%",
        margin:2,
        justifyContent: 'center'
    },
    btn3:{
        flex: 1,
        alignItems: 'center',
        backgroundColor: '#707B7C',
        borderRadius:"50%",
        margin:2,
        justifyContent: 'center'
    },
    btn4:{
        flex: 2,
        
        backgroundColor: '#707B7C',
        borderRadius:40,
        margin:2,
        justifyContent: 'center'
    },
    txt2:{
      fontSize: 30,
      alignSelf: 'center',
      
    },
    txt1:{
      fontSize: 30,
      alignSelf: 'center', 
      color:'#ECF0F1'
    },
    txt4:{
      fontSize: 30,
      marginLeft:30,
      color:'#ECF0F1'
    },
        })