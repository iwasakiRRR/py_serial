#!/usr/bin/env python
# -*- coding: utf-8 -*-  

import rospy
import serial
import sys
from std_msgs.msg import Int32

pub = rospy.Publisher("serial_topic", Int32, queue_size=1)

def main():
	rospy.init_node('py_serial')
	
	while not rospy.is_shutdown():

		ser = serial.Serial('/dev/ttyACM1', 9600)
		dist = ser.readline()
		ans = 999
		if dist == '999.00\r\n':
			hoge = 999;
		else:
			if dist[3] == '.':
				one = ChangeChar(dist[0])
				two = ChangeChar(dist[1])
				three = ChangeChar(dist[2])
				ans = one * 100 + two * 10 + three
				pub.publish(ans)
			elif dist[2] == '.':
				one = ChangeChar(dist[0])
				two = ChangeChar(dist[1])
				ans = one *10 + two
				pub.publish(ans)
			elif dist[1] == '.':
				ans = ChangeChar(dist[0])
				pub.publish(ans)
			else:
				hoge = 999
				print "何も受け取っていません①"
		print ans

def ChangeChar(c):
	#print c
	if c == '0':
		num = 0
	elif c == '1':
		num = 1
	elif c == '2':
		num = 2
	elif c == '3':
		num = 3
	elif c == '4':
		num = 4
	elif c == '5':
		num = 5
	elif c == '6':
		num = 6
	elif c == '7':
		num = 7
	elif c == '8':
		num = 8
	elif c == '9':
		num = 9
	else:
		hoge = 999
		print "何も受け取っていません②"
	return num

if __name__ == '__main__':

    main()

