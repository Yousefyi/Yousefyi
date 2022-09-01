- 👋 Hi, I’m @Yousefyi
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
Yousefyi/Yousefyi is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
const app = require ('express')
 require('./server')();

const { Client, MessageAttachment, Collection, MessageEmbed } = require('discord.js');
const bot = new Client({ disableMentions: 'everyone' });
const Discord = require("discord.js");
const client = new Discord.Client({ disableMentions: 'everyone' });
const botversion = require("./package.json").version;
client.login(process.env.token);
client.on("ready", () => {
  console.log(`Logged in as ${client.user.tag}!`);
});
let prefix = "*" // من هنا حدد البريفكس
  let ms = require("ms")
client.on("message", async (message) =>{
  const db = require("quick.db");
  if (message.author.bot || !message.guild) return;
	if (!message.content.startsWith(prefix) || message.author.bot) return;

	const args = message.content.slice(prefix.length).trim().split(/ +/);
	const command = args.shift().toLowerCase();
   if(message.content.startsWith(prefix + "تفعيل")) {
  var args2 = message.content.split(" ").slice(2).join(" ");
  if(!message.member.roles.cache.some(r => r.id == "<@&995701130896080916>")) return;
  if (!message.guild.member(client.user).hasPermission("MANAGE_ROLES"))return message.channel.send("I Must Have Premission Manage Roles");
  const user = message.guild.member( message.mentions.users.first() || message.guild.members.cache.get(args));
  if (!user) return message.channel.send("منشن شخص يا غبي لاصيدك");
  if(message.author.id == user.id) return message.channel.send("ما تقدر تعطي نفسك مستوى");
  if(message.guild.ownerID == user.id) return message.channel.send("ما تقدر تعطي الرتب المؤقتة للاونر شيب");
  let a = message.guild.roles.cache.find(role => role.id === "<@&996513931566780546>");
  let nota = message.guild.roles.cache.find(role => role.id === "<@&996512309755269261>");
  let nota1 = message.guild.roles.cache.find(role => role.id === "رتبه بتنشال");
  let a1 = message.guild.roles.cache.find(role => role.id === "رتبه بتجيه");
  let a2 = message.guild.roles.cache.find(role => role.id === "رتبه بتجيه");


  if(user.roles.cache.some(r=> r.id == a)) return message.channel.send("مفعل مسبقاٌ");
  message.guild.member(user).roles.add(a)
  message.guild.member(user).roles.remove(nota)
  message.guild.member(user).roles.remove(nota1)
  message.guild.member(user).roles.add(a1)
  message.guild.member(user).roles.add(a2);
let giveembed = new MessageEmbed()
.setAuthor(client.user.tag,client.user.avatarURL)
.setColor("RED")
.setThumbnail(`https://images-ext-2.discordapp.net/external/4E2pxy76bhGRSsXDrcGJSbpbaKXIzPOz623DPFI7_QQ/%3Fsize%3D2048/https/cdn.discordapp.com/icons/690987445369438229/a_a5138be1dc026de7c561202ae3d5d88d.gif?width=559&height=559`)
.setDescription(`${message.author.tag} بواسطة  ${user} تم تفعيل `)

message.channel.send(giveembed).then(() => {
              let rezrc = db.fetch(`rezrchannel_${message.guild.id}`)
            if (!rezrc) return;
            let rezr = new MessageEmbed()
    .setAuthor(`لوق التفعيل`, message.guild.iconURL())
    .setColor("RED")
    .setFooter(message.guild.name, message.guild.iconURL())
    .addField("**الوصف**", "تفعيل")
    .addField("**تم تفعيل**", user)
    .addField("**بواسطة**", `${message.author.tag}`)
    .addField("**التاريخ**", message.createdAt.toLocaleString())
    .setTimestamp()
            var sChannel = message.guild.channels.cache.get(rezrc)
            if (!sChannel) return;
            sChannel.send(rezr).then(() => {
  let useremebed = new MessageEmbed()
.setAuthor(client.user.tag, client.user.avatarURL)
.setColor("RED")
.setThumbnail(`https://images-ext-2.discordapp.net/external/4E2pxy76bhGRSsXDrcGJSbpbaKXIzPOz623DPFI7_QQ/%3Fsize%3D2048/https/cdn.discordapp.com/icons/690987445369438229/a_a5138be1dc026de7c561202ae3d5d88d.gif?width=559&height=559`)
.setDescription(` تم تفعليك ونورت السيرفر, ${user} مرحبا  `)
  user.send(useremebed)






})})
      
       
             }});

const db = require("quick.db")
  client.on("message", async (message) =>{
  if (message.author.bot) return;
  if(message.content.toLowerCase.split(" ")[0] === `${prefix}set-channel،`){
   if (!message.guild.member(message.author).hasPermission("MANAGE_GUILD")) return  message.channel.send(new Discord.MessageEmbed().setDescription("You dont have permission `MANAGE_GUILD`").setColor("#00BFFF"))
  if (!message.guild.member(message.client.user).hasPermission("MANAGE_GUILD")) return;
  let channel = message.mentions.channels.first() 
  if(!channel) {
  return message.channel.send(new Discord.MessageEmbed().setColor(`#00BFFF`).setFooter(`Requested By: ${message.author.tag}`, message.author.avatarURL({dyanmic:true})).setDescription("Please Mention the channel first"))}
   db.set(`rezrchannel_${message.guild.id}`, channel.id) 
  message.channel.send(new Discord.MessageEmbed().setFooter(`Requested By: ${message.author.tag}`, message.author.avatarURL({dynamic: true})).setColor(`#00BFFF`).setDescription(`Channel is setup as ${channel}`)) 
  }})



client.on("ready", () =>{

console.log(`${client.user.tag} Is Available`);
client.user.setActivity("online", {type: "STREAMING", url: "https://twitch.tv/random"})


})











// أوامر السجن 

client.on("message", async (message) =>{
  const db = require("quick.db");
  if (message.author.bot || !message.guild) return;
	if (!message.content.startsWith(prefix) || message.author.bot) return;

	const args = message.content.slice(prefix.length).trim().split(/ +/);
	const command = args.shift().toLowerCase();
   if(message.content.startsWith(prefix + "سجن")) {
  var args2 = message.content.split(" ").slice(2).join(" ");
  if(!message.member.roles.cache.some(r => r.id == "1014908597097988146 ")) return;
  if (!message.guild.member(client.user).hasPermission("MANAGE_ROLES"))return message.channel.send("I Must Have Premission Manage Roles");
  const user = message.guild.member( message.mentions.users.first() || message.guild.members.cache.get(args));
  if (!user) return message.channel.send("منشن شخص عشان اسجنه , ما منك فايدة");
  if(message.author.id == user.id) return message.channel.send("ما تقدر تسجن نفسك , مافي عقل");
  if(message.guild.ownerID == user.id) return message.channel.send("ما تقدر تعطي الرتب المؤقتة للاونر شيب");
  let ro = message.guild.roles.cache.find(role => role.id === "رتبه بتنشال"); 
  let ro1 = message.guild.roles.cache.find(role => role.id === "رتبه بتنشال");
  let ro2 = message.guild.roles.cache.find(role => role.id === "رتله بتنشال"); 
  let ro3 = message.guild.roles.cache.find(role => role.id === "رتبه بتنشال"); 
  let ro4 = message.guild.roles.cache.find(role => role.id === "رتبه بتنشال");
  let ad = message.guild.roles.cache.find(role => role.id === "رتبه بتجيه");
  let ad1 = message.guild.roles.cache.find(role => role.id === "رتبه بتجيه");

  if(user.roles.cache.some(r=> r.id == ad)) return message.channel.send("مسجون مسبقاٌ");
  message.guild.member(user).roles.remove(ro)
  message.guild.member(user).roles.remove(ro1)
  message.guild.member(user).roles.remove(ro2)
  message.guild.member(user).roles.remove(ro3)
  message.guild.member(user).roles.remove(ro4)
  message.guild.member(user).roles.add(ad)
  message.guild.member(user).roles.add(ad1)

  let give1embed = new MessageEmbed()
.setAuthor(client.user.tag,client.user.avatarURL)
.setColor("RED")
.setThumbnail(`https://images-ext-2.discordapp.net/external/4E2pxy76bhGRSsXDrcGJSbpbaKXIzPOz623DPFI7_QQ/%3Fsize%3D2048/https/cdn.discordapp.com/icons/690987445369438229/a_a5138be1dc026de7c561202ae3d5d88d.gif?width=559&height=559`)
.setDescription(`${message.author.tag} بواسطة  ${user} تم سجن `)

message.channel.send(give1embed).then(() => {
              let rezrc1 = db.fetch(`rezr1channel_${message.guild.id}`)
            if (!rezrc1) return;
            let rezr1 = new MessageEmbed()
    .setAuthor(`لوق السجن`, message.guild.iconURL())
    .setColor("RED")
    .setFooter(message.guild.name, message.guild.iconURL())
    .addField("**الوصف**", "**سجن**")
    .addField("**تم سجن**", user)
    .addField("**بواسطة**", `${message.author.tag}`)
    .addField("**التاريخ**", message.createdAt.toLocaleString())
    .setTimestamp()
            var sChannel = message.guild.channels.cache.get(rezrc1)
            if (!sChannel) return;
            sChannel.send(rezr1)






})}
      
       
             });
  client.on("message", async (message) =>{
  if (message.author.bot) return;
  if(message.content.toLowerCase().split(" ")[0] === `${prefix}set-sgn`){
   if (!message.guild.member(message.author).hasPermission("MANAGE_GUILD")) return  message.channel.send(new Discord.MessageEmbed().setDescription("You dont have permission `MANAGE_GUILD`").setColor("#00BFFF"))
  if (!message.guild.member(message.client.user).hasPermission("MANAGE_GUILD")) return;
  let channel = message.mentions.channels.first() 
  if(!channel) {
  return message.channel.send(new Discord.MessageEmbed().setColor(`#00BFFF`).setFooter(`Requested By: ${message.author.tag}`, message.author.avatarURL({dyanmic:true})).setDescription("Please Mention the channel first"))}
   db.set(`rezr1channel_${message.guild.id}`, channel.id) 
  message.channel.send(new Discord.MessageEmbed().setFooter(`Requested By: ${message.author.tag}`, message.author.avatarURL({dynamic: true})).setColor(`#00BFFF`).setDescription(`Channel is setup as ${channel}`)) 
  }})
